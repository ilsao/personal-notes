
# 前言

筆者最近在寫 xv6 的 lab，閱讀 xv6 book 後仍對 xv6 的陷入機制感到迷惑。在統整 xv6 book 中的內容與詢問 GPT 的答案後，便產出此篇文章。

因為筆者仍是新手，錯誤之處請各位師傅指正，謝謝！

# 前置知識

xv6 的進程空間：

![[Pasted image 20250829145820.png]]

**硬件線程(hardware thread, hart)**：處理器核心中的一個執行單元。

**per-CPU**：每個核的資料。

**控制與狀態寄存器 (Control and Status Register, CSR)**：存放一些能改變 CPU 行為的**控制**，並反映處理器目前的**狀態**。

**trampoline**：其中存放 `uservec` 與 `userret` 的匯編代碼，幫助從用戶模式切換為內核模式或從內核模式返回到用戶模式。內核與每個進程都將 trampoline 映射到同一虛擬地址上，使得頁表從一個模式切換到另一個模式後，對 trampoline 虛擬地址的訪問不會造成 page fault。參考：[trampoline.S](https://github.com/mit-pdos/xv6-riscv/blob/riscv//kernel/trampoline.S)。

**trapframe**：存放使用者寄存器，還有與進程相關的內核棧、`hartid`、`usertrap`地址、內核頁表地址等資訊，其地址由 `TRAMPOLINE` 定義。參考[proc.h](https://github.com/mit-pdos/xv6-riscv/blob/riscv/kernel/proc.h#L43)。

# 陷入機制

以下為陷入機制使用的 CSR 寄存器：
- `stvec`：內核在此放置陷阱處理程序的地址。
- `sepc`：發生陷阱時，舊的 pc 值會保存在此，`sret` 會將 `sepc` 複製到 pc 從而從陷阱返回。
- `scause`：存放引起陷阱的原因。
- `sscratch`：保存 per-CPU 的 `struct cpu*` 指針。
- `sstatus`：其中 `SIE` 位控制設備中斷是否啟用，`SPP` 位保存陷阱是來自用戶還是管理模式，並控制 `sret` 的返回模式。

當執行陷阱(除去計時器中斷)時，RISC-V 執行以下操作：
1. 若陷阱是設備中斷，且 SIE 被清空，則不執行以下操作。
2. 清除 SIE 禁止中斷，防止處理程序被打斷。
3. 將 pc 複製到 `sepc`。
4. 將當前模式(用戶或管理)保存在狀態的 SPP 位中。
5. 設置 `scause` 反映原因。
6. 將模式設置為管理模式。
7. 將 `stvec` 複製到 pc。
8. 跳轉到 pc 運行。

當硬件執行完以下操作，交由軟件(xv6)處理剩餘操作。

xv6 從用戶模式陷入內核模式與返回的過程(`uservec -> usertrap -> prepare_return -> userret`)：
1. 當執行用戶代碼時，`stvec` 指向 `uservec` (即 trampoline.S 中協助從用戶模式陷入內核的匯編碼)，所以一旦需要陷入內核就會跳轉到 `uservec` 中。
2. `uservec` 在 `trampoline` 中保存用戶寄存器，以免進入內核時修改這些值。`uservec` 將 `trampoline` 保存在 `sscratch` 中。
3. 從 `p->trapframe->kernel_satp` 中取得內核頁表，將 `satp` 切換為內核頁表並調用 `usertrap` (`p->trapframe->kernel_trap`)。`usertrap` 參考：[trap.c](https://github.com/mit-pdos/xv6-riscv/blob/riscv/kernel/trap.c#L37)
4. `usertrap` 會確認陷阱的原因，處理並返回。`usertrap` 會修改 `stvec` 指向 `kernelvec`，因為此時系統處於內核模式，所以所有中斷與異常都由都由 `kerneltrap` 處理。
5. 當以上處理結束，會調用 `prepare_return`。由 `trap.c` 返回到 `trampoline.c` 中的 `userret`。
6. `userret` 會讀出保存的用戶寄存器，並切換頁表回用戶模式。

# 系統調用

以下用對 `exec` 的調用說明。

用戶代碼會將參數存在 `a0, a1` 中，然後將系統調用號存放在 `a7`。`syscall` 將返回值存放在 `a0`。系統調用號的定義存放在：[syscall.h](https://github.com/mit-pdos/xv6-riscv/blob/riscv/kernel/syscall.h)。

參考：[syscall.c](https://github.com/mit-pdos/xv6-riscv/blob/riscv//kernel/syscall.c#L132)。