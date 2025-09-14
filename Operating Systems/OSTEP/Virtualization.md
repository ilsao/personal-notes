
# 前言

本書有部分筆記與 CSAPP 中重疊，重疊部分筆記請查找 CSAPP 篇。

# 受限直接執行

The crux of the problem: **如何高效、可控的控制虛擬化CPU？**

**受限直接執行(Limited Direct Execution, LDE)**：事先設置好硬件，使得程序在受限的情況下直接在 CPU 上運行。

LDE 有兩個階段：
- 系統引導：開機時，內核初始化陷阱表，使 CPU 記住它的位置以供未來使用。
- 運行進程：當執行陷阱返回指令時，CPU 會從內核棧恢復寄存器，切換到用戶模式，並跳轉到 PC 指向處。

操作系統為保持對 CPU 的控制權，採用**時鐘中斷(timer interrupt)** 。時鐘設備每隔幾毫秒產生一次中斷，使得控制轉移到內核中斷處理程序。這時操作系統重新獲得 CPU 控制權，可以做任何想做的事：停止進程、創建另一個進程。

上下文切換：當時鐘中斷，且 OS 決定執行上下文切換時會發生以下事情：
- 硬件：將寄存器A保存到內核棧A
- 處理程序：
	- 調用 `switch()` 例程：
		將寄存器A保存到進程結構A。將進程結構B恢復到寄存器B。
	- 從陷阱返回到進程B

以上過程看似無意義的保存兩次上下文信息，但其含義不同。

想像以下場景：當要重新調度A時，要對B執行上下文切換。但因為A不在運行，所以 CPU 不知道內存棧A的位置信息，必須通過進程結構A才能獲取該信息。所以有必要保存兩次上下文信息，且兩次保存的信息有些許不同。

# 進程調度

# Intro.

調度的性能指標：**周轉時間(turnaround time)**。即，進程從進入系統到完成執行所花的總時間：

$$
T_{turnarond}=T_{completion} - T_{arrival}
$$

**先進先出(FIFO，又稱 First Come First Served, FCFS)**：先到達系統的作業先被調度。缺點：若先到達的作業運行時間長，導致後面運行時間短的作業等待較久，平均周轉時間長。

> [!Note] 護航效應
> **護航效應(convoy effect)**：指的是消耗資源較多者排在了消耗資源較少者的前面，導致後者等待時間較長的現象。

**最短任務優先(Shortest Job First, SJF)**：若假設所有作業同時到達，可證明 SJF 是最優(optimal)的調度算法。但考慮運行時間較長的作業最早到達，運行到一半時運行時間較短的作業才到達。此時，運行時間短的作業仍被迫等待。

**最短完成時間優先(Shortest Time-to-Completion First, STCF)** 或 **搶佔式最短作業優先(Preemptive Shortest Job First, PSJF)**：每當新作業進入系統，就會判斷剩餘作業與新作業中誰的剩餘時間較短，然後調度該作業。

新度量指標：**響應時間(response time)**。即，進程從到達系統到首次執行所需的時間：

$$
T_{response} = T_{first\_{}run}-T_{arrival}
$$

**輪轉(Round-Robin, RR)**：每個**時間片(time slice，又稱調度量子, scheduling quantum)** 內運行一個作業，到達下個時間片就調度。雖然時間片長度越短，RR的響應時間越短，但須考慮上下文切換所耗的時間。我們必須權衡時間片長度，以攤銷(amortize)該成本。缺點：周轉時間差。

> [!Warning]
> 注意：時間片長度必須是時鐘周期的倍數。

## 多級反饋隊列

**多級反饋隊列(Multi-level Feedback Queue, MLFQ)**：使用多個優先級對列分類、調度程序。

MLFQ有以下規則：
- 若A的優先級 > B，則先運行A。
- 若A的優先級 = B，則輪轉調度。
- 作業剛進入系統時，處於最高優先級對列中。
- 當作業用完在該層的**時間配額**，無論放棄多少次 CPU ，都降低其優先級(移入低一級對列)。
	若作業運行時間短，在降低優先級前就會運行完，使得 MLFQ 趨近 SJF。
	防止 I/O 密集型作業卡時間放棄 CPU，使得一直處於高優先級。
- 每過一段時間，將系統所有作業提升到最高優先級。
	避免運算密集型作業長期處於低級，而無法被調度。

## 比例份額

**比例份額(proportional-share，或稱公平份額, fair-share)**：假定了每個作業有一些彩票，根據各進程的彩票數來調度程序。

彩票調度：
- 使用鏈表紀錄作業擁有的票數，票數較多者在鏈表較前方。
	保證尋找過程效率。
- 從 0 ~ 總票數-1 中隨機選數字，誰的加總票數包含此數，就被調度。

步長調度：
- 每個作業擁有一個步長，該值為彩票數的反比。
- 使用一個計數器(稱行程值 pass)紀錄總體進展。
- 調度器選擇行程值最小者，運行一段時間，並使計數器+=行程值。

兩個策略都有一個缺點，調度器沒有策略自動分配彩票。所以使用此種方法的前提是，用戶清楚知道，並設置每個作業所佔的份額比例。

## 多處理器調度

**緩存親合度(cache affinity)**：一個進程在某 CPU 上運行時，會在該 CPU 上緩存許多狀態。下次該進程在此 CPU 上運行時，由於存在緩存所以會運行得更快。在多處理器調度上，應考慮緩存親合度，使進程盡量保持在同個 CPU 上。

**單隊列調度(Single Queue Multiprocessor Scheduling, SQMS)**：簡單的將單 CPU 的策略搬到多 CPU 上，總共僅維護一個對列，所有 CPU 共享。
	親合度機制：
		盡量讓進程在同個 CPU 上運行。保持某些作業親合度的同時，可能需要犧牲其他作業的親合度來均衡負載。
		比如有4個 CPU 與5個作業需要調度，可能會發生以下情況：
		0：A E A A A
		1：B B E B B
		2：C C C E C
		3：D D D D E
		犧牲了E的親合度讓其他作業保持親合度。
	數據共享與同步：
		需要鎖以保證原子性，需要額外的時間開銷。

**多隊列調度(Multi-Queue Multiprocessor Scheduling, MQMS)**：MQMS 與 SQMS 不同的是，每個 CPU 都維護一個專屬的隊列，且不同隊列可以使用不同策略調度。由於每個 CPU 調度之間獨立，可以顯著的避免數據共享與親合度問題。
- **遷移(migration)** 與 **工作竊取(work stealing)**：
	隊列會不斷檢查其他隊列，當兩隊列之間任務數差距過大，較小者會從較大者處竊取一個或多個作業，使得負載均衡。這種行為就稱工作切確，而作業從一個隊列轉移到另一個隊列的過程稱遷移。

# 虛擬內存

> [!Warning] 注意
> 此部分本文大量精簡，更多詳細信息請參考：[CSAPP U9 筆記](https://ilsao.github.io/2025/08/06/CSAPP-U9-%E7%AD%86%E8%A8%98%E8%88%87%E7%B7%B4%E7%BF%92%E9%A1%8C%E8%A7%A3%E7%AD%94/)

虛擬內存系統的目標：
1. **透明(transparency)**：使得程序無法感知內存虛擬化。
2. **效率(efficiency)**：時間上不使得程序變慢，空間上不需要額外內存支持。
3. **保護(protection)**：進程之間**隔離(isolation)**，互不影響。

基址寄存器：存放進程被加載到的地址數據。

界限寄存器：進程地址的最大偏移量。與基址寄存器相加可以得到映射後的最大物理地址。

所以映射到物理地址的公式為：

``` C
physical address = base + virtual address
```

## 分段

分段：避免直接將整個地址空間映射到物理內存上，使得堆和棧之間的空閒區域也被映射而佔據內存。

通常地址空間分為段：代碼、棧、堆。每個段都維護自己的基址和界限寄存器。使得我們需要 MMU 的硬件支持一組3對這樣的寄存器。

**粗粒度(coarse grained)**：將地址空間分為少量較大的段，如上假設。

**細粒度(fine grained)**：將地址空間分為大量較小的段。

對於棧和堆的映射，我們不可以直接將基址加上虛擬地址。必須先將虛擬地址減去堆或棧的虛擬地址，得到該數據在堆或棧為起始的偏移，再加上基址。

**如何判斷地址屬於哪個段**？有一種常見的方式，稱為**顯式(explicit)** 方式：

如上假設，我們有三個段，所以需要兩位來表示。我們將高兩位當作段標示，剩餘位表示段內偏移量。這樣我們就可以寫出如下地址轉換代碼：

``` C
segment = (virtual_addr & SEG_MASK) >> SEG_SHIFT
offset = virtual_addr & OFFSET_MASK
if (offset >= bound[segment])
	raise_exp(PROTECTION_FAULT)
else
	phys_addr = base[segment] + offset
	register = access_mem(phys_addr)
```

**如何映射棧？** 硬件必須多紀錄一位，即是否正向增長。然後我們還必須正確處理反向偏移：將段內偏移減去段大小，就可以正確得到反向偏移。

**如何支持共享？** 通過額外紀錄一個保護位，就可以隔離破壞從而實現共享。

**操作系統如何支持分段？** 需要考慮以下兩點：
1. 上下文切換時，各個段寄存器的值必須被保存和恢復。
2. 若地址空間大小不一，會導致外部碎片的問題。

## 分頁

分段有很大的問題，即容易造成外部碎片。所以出現了第二種方法：分頁。

**頁表存放在哪裡？** 頁表存在內存中，CR3/satp 寄存器存放著指向頁表的基址。

**物理地址索引緩存(physically-indexed cache)**：先將虛擬地址轉換為物理地址，再去查找緩存。因為可能有多個虛擬地址映射到同個物理地址上，所以**若使用虛擬地址讀寫緩存，可能造成緩存一致性出現問題**。

Why？如果緩存僅在被驅逐時將數據寫回，當某虛擬地址映射到物理地址A，並於A處修改了緩存B，在另一個同樣被映射到A的虛擬地址訪問緩存C時，因為緩存B還未寫回，緩存C返回了未更新的數據，導致緩存一致性出現問題。

讓我們介紹一下儲存在 PTE 中的一些位的作用：
- **有效位(valid bit)**：所有未使用的空間都被標示為無效，訪問這些無效的頁會導致異常。
- **保護位(protection bit)**：表明是否可讀、寫、執行。
- **存在位(present bit)**：表示該頁在內存還是在磁盤上。
- **髒位(dirty bit)**：表示頁進入內存後是否被修改過。
- **參考位(reference bit，或稱訪問位, accessed bit)**：追蹤頁是否被訪問。

**誰來處理 TLB 未命中？** 對於 CISC 指令集，硬件處理。對於 RISC 指令集，操作系統處理。

為了避免 TLB 未命中引起的無限遞歸，有以下兩種方法：
- 將處理程序直接存放在物理內存中，而無須映射。
- 在 TLB 中保留一些條目專門存放處理程序，這些**被監聽的 (wired)** 地址總會被命中。

> [!Warning] 注意
> - VPN 與 PFN 會同時存在於 TLB 中，因為 TLB 是**全相聯(fully associative)** 的緩存，所以必須有 VPN 來標示映射的頁面。
> - TLB 的有效位 != 頁表的有效位。

> [!Note] PFN 與 PPA 的差別
> PFN 全稱 Physical Frame Number，指的是物理頁幀的編號。
> PPA 全稱 Physical Page Address，指的是物理頁幀的地址。
> 所以 PPA = PFN << offset。

**上下文切換時 TLB 怎麼辦？** 有兩種解決方法：
1. 上下文切換時，將 TLB 每一項的有效位都設置成零，從而清空 TLB。這種方法可以由操作系統或硬件來執行。
2. 向 TLB 添加一個**地址空間標示符(Address Space Identifier, ASID)**，以標示此條目屬於哪個進程。此方法使得可以跨上下文切換來共享 TLB。

> [!Warning] 注意
> 不管如何，操作系統必須在上下文切換時修改頁表基址寄存器(PTBR)的值。

## 較小的頁表

**Why?** 因為對整個地址空間分頁，仍有**未使用空間卻佔據頁表條目**的問題。

法一 **分段 + 分頁**：
	在此方法中，我們為每個段都分配一個頁表。比如為代碼、棧、堆提供三個頁表。
	在此方法中的基址與界限寄存器指向的是相應段的頁表與結尾。
	我們仍使用**顯式**方法來識別虛擬地址屬於哪段(取高地址兩位做段標示)。
	**Cons**：外部碎片多
	當 TLB 未命中時，使用以下方法取得 PTE：

``` C
SN       = (virtual_addr & SEG_MASK) >> SN_SHIFT
VPN      = (virtaul_addr & VPN_MASH) >> VPN_SHIFT
pte_addr = base[SN] + (VPN * sizeof(PTE))
```

法二 **多級頁表**：
	此處我們以二級頁表說明。
	二級頁表由一個頁目錄與多個頁表組成，一個**頁目錄項(Page Directory Entries)** 指向一個頁表(用**頁幀號(Page Frame Number, PFN)** 表示)。
	當 PDE 的有效位為一時，代表其指向的頁表中至少有一個 PTE 的有效位為一。
	**Cons**：TLB 未命中時，需要從內存中加載兩次，一次頁目錄，一次頁表。(注：TLB 中存放的仍是 VPN 與 物理地址的映射)
	多級頁表屬於**時間-空間折中(time-space trade-off)** 的例子。

**超過二級？** 使用更多級的頁表是有必要的，若使用二級頁表後發現頁目錄表仍然過大，可以考慮繼續拆分成更多級的頁表。

法三 **反向頁表(inverted page table)**：
	系統不為所有進程分頁表，而是所有進程共享一個頁表。其中，頁表項存儲頁幀到 (進程，虛擬頁) 的映射。因為線性查表較慢，通常使用**哈希表**作為查找的數據結構。

## 超越物理內存

**交換空間(swap space)**：在硬盤上開闢的一塊供物理頁移入移出的空間。

**存在位(present bit)**：如果存在位(在 PTE 中)為1，則該頁處於物理內存中，否則，在硬盤上。訪問在硬盤上的頁則稱為**頁錯誤(page fault)**，或稱**缺頁**。

**缺頁**：操作系統會用 PTE 中的某些位來存儲硬盤地址。缺頁發生時一律由操作系統提供的缺頁處理程序處理，處理程序通過查找 PTE 來請求頁。當 I/O 完成後，處理程序會更新存在位與 PFN 以記錄獲取的內存地址，並重新執行指令。下一次重新訪問 TLB 仍舊不會命中，但由於存在位為1，所以會將頁表中的地址更新到 TLB 中。

訪問虛擬地址時，硬件算法如下：

``` C
VPN = (VirtualAddress & VPN_MASK) >> SHIFT
(Success, TlbEntry) = TLB_Lookup(VPN)
if (Success)
	if (CanAccess(TlbEntry.ProtectBits))
		Offset = VirtualAddress & OFFSET_MASK
		PhysAddr = (TlbEntry.PFN << SHIFT) | Offset
		Register = AccessMemory(PhysAddr)
	else
		RaiseException(PROTECTION_FAULT)
else
	PTEAddr = PTBR + (VPN - sizeof(PTE))
	PTE = AccessMemory(PTEAddr)
	if (!PTE.Valid)
		RaiseException(SEGMENTATION_FAULT)
	else
		if (!CanAccess(PTE.ProtectBits))
			RaiseException(PROTECTION_FAULT)
		else if (PTE.Present)
			TLB_Insert(VPN, PTE.PFN, PTE.ProtectBits)
			RetryInstruction()
		else if (!PTE.Present)
			RaiseException(PAGE_FAULT)
```

缺頁時操作系統算法如下：

``` C
PFN = FindFreePhysicalPage()
if (PFN == -1)
	PFN = EvictPage()
DiskRead(PTE.DiskAddr, pfn)
PTE.present = True
PTE.PFN = PFN
RetryInstruction()
```

**頁交換何時發生？** 操作系統設置了**高水位線(High Watermark, HW)** 和 **低水位線(Low Watermark, LW)**。當少於 LW 個頁可用，後台線程就會釋放內存直到有 HW 個可用的物理頁。

**分段 FIFO**：
	**駐留集大小(Resident Set Size, RSS)**：每個進程可以保存在內存中的最大頁數。
	當某進程超過其 RSS 時，最先進入的頁被驅逐到**全局的二次機會列表(second-chance list)**。二次機會列表分為乾淨空閒列表和髒頁列表，頁會根據其髒位放入相對應的列表尾部。
	若另一個進程Q需要一個空閒頁，它會從全局乾淨列表取出第一個空閒頁。若原來的進程P在回收某頁之前在該頁上發生缺頁，則會將該頁從列表中回收。

**近似 LRU** ：
- clock algorithm
	給所有頁添加一個使用位，當該頁被訪問時設置為1。
	所有頁串成一個循環鏈表，當系統需要驅逐頁時，時鐘指針開始掃描此鏈表。
	當指針指向的節點的使用位為0，表示該頁很久未使用，可以驅逐。當指針指向的節點使用位為1，則將該節點使用位設置為0，並向前遞進。
- clock algorithim 變種：逐個掃描節點 -> 隨機選取節點。

**考慮髒頁**：因為被修改過的頁在被驅逐時需要將其寫回磁盤，需要花費較久時間。考慮引入一個**修改位(modified bit，又稱髒頁, dirty bit)**，紀錄。clock algorithm 可以再新增一個變種，比如優先驅逐未被修改的頁。

**從虛擬地址映射到物理地址的順序如下**：
1. 解析虛擬地址 → 得到 VPN 和 VPO。
2. 查找 TLB 是否命中。
	- 命中 → 直接用 PFN 合成 PA，完成！。
	- 未命中 → 執行以下步驟。
3. 用 VPN 查頁表 → 得到 PTE。
	- 檢查 valid bit。
	- 若無效 → 缺頁處理(頁存在磁盤上)或終止進程(訪問非法地址)。
4. 從 PTE 中取得 PFN。
5. 更新 TLB。
6. 合成 PA = PFN + VPO。