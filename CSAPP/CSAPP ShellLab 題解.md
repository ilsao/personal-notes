
# 前言

此lab要求實現一個帶作業控制的tiny shell，涉及到並發。推薦讀者完整閱讀過一次CSAPP第八章的內容再嘗試此lab。

# 取得lab

在[此處](https://csapp.cs.cmu.edu/3e/shlab-handout.tar)取得lab文件，在[此處](http://csapp.cs.cmu.edu/3e/shlab.pdf)取得官方文檔。

利用命令`tar xvf shlab-handout.tar`解壓文件。

以下所有代碼皆在`tsh.c`中編寫。
# 實驗要求

* 用戶輸入的命令行包含一個`name`及零或多個參數，參數由單或多個空格分隔。若`name`是一個內置命令，則tsh(tiny shell的簡稱)應立即響應並等待下條命令。否則，應將`name`視為可執行文件的路徑，tsh應將其加載並運行在子進程上下文中。
* 輸入`ctrl+c`(`ctrl+z`)會發送一個`SIGINT`(`SIGTSTP`)到前台作業以及其子進程中。若沒有任何前台作業，則信號應不產生任何效果(不能影響tsh)。
* 若命令行末尾包含`&`，則將命令運行在後台，否則運行在前台。
* 每個作業都可以用PID或JID識別。JID應用前輟`%`標示，PID則不用任何前輟。
* tsh應支持以下內置命令：
	* `quit`：退出tsh。
	* `jobs`：列出所有作業。
	* `bg <job>`：傳送給`job`(可用PID或JID指定)一個`SIGCONT`信號，並將該作業運行在後台。
	* `fg <job>`：傳送給`job`(可用PID或JID指定)一個`SIGCONT`信號，並將該作業運行在前台。
* tsh應回收所有殭死(屍)進程。

# 開始編寫

以下是我們需要實現的函數：
* `eval`：解析命令行。
* `built_cmd`：運行內置命令。
* `do_bgfg`：實現`bg`和`fg`指令。
* `waitfg`：掛起tsh並等待前台作業。
* `sigchld_handler`：處理`SIGCHLD`信號。
* `sigint_handler`：處理`SIGINT`信號。
* `sigtstp_handler`：處理`SIGTSTP`信號。

## 錯誤處理包裝函數

為了避免每次調用系統函數前手動編寫錯誤處理代碼，我們使用包裝函數替代。

``` C
 /* Sigprogmask - Wrapper for sigprocmask funciton */
int Sigprocmask(int how, sigset_t *set, sigset_t *oldset)
{
    int success;
    if ( (success = sigprocmask(how, set, oldset)) < 0 )
        unix_error("sigprocmask error");
    return success;
}

/* Fork - Wrapper for sigprocmask function */
int Fork()
{
    pid_t pid;
    if ( (pid = fork()) < 0 )
        unix_error("fork error");
    return pid;
}

/* Execve - Wrapper for execve function */
int Execve(const char *filename, const char **argv, const char *envp[])
{
    int success;
    if ( (success = execve(filename, argv, envp)) < 0) {
        printf("%s: Command not found\n", filename);
        exit(0);
    }

    return success;
}

/* Sigemptyset - Wrapper for sigemptyset function */
int Sigemptyset(sigset_t *set)
{
    int success;
    if ( (success = sigemptyset(set)) < 0)
        unix_error("sigemptyset error");
    return success;
}

/* Sigfillset - Wrapper for sigfillset function */
int Sigfillset(sigset_t *set)
{
    int success;
    if ( (success = sigfillset(set)) < 0)
        unix_error("sigfillset error");
    return success;
}

/* Sigaddset - Wrapper for sigaddset function */
int Sigaddset(sigset_t *set, int signum)
{
    int success;
    if ( (success = sigaddset(set, signum)) < 0)
        unix_error("sigaddset error");
    return success;
}

/* Kill - Wrapper for kill function */
int Kill(pid_t pid, int sig)
{
    int success;
    if ( (success = kill(pid, sig)) < 0 && errno != ESRCH)
        unix_error("kill error");
    return success;
}
```

## `eval`

通過閱讀提供的helper函數，我們可以知道`parseline`在解析命令行的同時，會將該命令是否指定運行在後台作為返回值傳回。我們將返回值存放在`bg`中。

然後調用`builtin_cmd`(等下編寫)確認是否為內置命令。

若不是內置命令，我們需要`fork`一個子進程出來，然後利用`execve`運行程序在其上下文中。注意，執行`fork`前需要先阻塞`SIGCHLD`信號，直到執行完`addjob`才恢復。避免因為競爭導致添加了無法刪除的作業。想像這種流程，在子進程`fork`出來後直接運行，並在控制流傳遞給父進程前執行完畢並發送`SIGCHLD`信號。此時父進程收到信號並回收子進程，然後再調用`addjob`添加一個已經被回收的作業，導致該作業永遠不會被刪除。為了避免該狀況，我們需要阻塞信號。

還需要注意的是，為了避免傳信號給子進程時也將信號傳給tsh，我們使用`setpgid(0, 0)`創建一個新進程組並將子進程添加進去。

最後，如果是前台進程則調用`waitfg`掛起tsh直到前台作業返回，否則不掛起tsh在後台運行作業。

``` C
/* 
 * eval - Evaluate the command line that the user has just typed in
 * 
 * If the user has requested a built-in command (quit, jobs, bg or fg)
 * then execute it immediately. Otherwise, fork a child process and
 * run the job in the context of the child. If the job is running in
 * the foreground, wait for it to terminate and then return.  Note:
 * each child process must have a unique process group ID so that our
 * background children don't receive SIGINT (SIGTSTP) from the kernel
 * when we type ctrl-c (ctrl-z) at the keyboard.  
*/
void eval(char *cmdline) 
{
    char *argv[MAXARGS];
    int bg = parseline(cmdline, argv);  /* background job? */
    int builtin = builtin_cmd(argv);    /* is built-in command? */

    sigset_t mask_one, mask_all, prev;

    Sigemptyset(&mask_one);
    Sigaddset(&mask_one, SIGCHLD);
    Sigfillset(&mask_all);

    if (!builtin) {
        Sigprocmask(SIG_BLOCK, &mask_one, &prev);   /* block SIGCHLD */
        pid_t pid;

        if ( (pid = Fork()) == 0 ) {                /* child process */
            Sigprocmask(SIG_SETMASK, &prev, NULL);  /* unblock SIGCHLD */
            setpgid(0, 0);
            Execve(argv[0], argv, environ);
        }

        Sigprocmask(SIG_BLOCK, &mask_all, NULL);   /* block all signals for atomic operation */
        if (bg) {
            addjob(jobs, pid, BG, cmdline);
            struct job_t *j = getjobpid(jobs, pid);
            printf("[%d] (%d) %s", j->jid, j->pid, j->cmdline);
        }
        else {
            addjob(jobs, pid, FG, cmdline);
            waitfg(pid);
        }            
        Sigprocmask(SIG_SETMASK, &prev, NULL);      /* unblock SIGCHLD */
    }
    return;
}
```

## `builtin_cmd`

直接上代碼，簡單直接。

``` C
/* 
 * builtin_cmd - If the user has typed a built-in command then execute
 *    it immediately.  
 */
int builtin_cmd(char **argv) 
{
    if (argv[0] == NULL)
        return 1;

    int builtin = 0;

    char *cmdlist[4] = {"quit", "jobs", "bg", "fg"};
    int idx = -1;

    int i;
    for (i = 0; i < 4; i++) {
        if (strcmp(argv[0], cmdlist[i]) == 0) {
            idx = i;
            builtin = 1;
        }
    }        

    switch (idx) {
    case 0:
        exit(0);
    case 1:
        listjobs(jobs);
        break;
    case 2:
        do_bgfg(argv);
        break;
    case 3:
        do_bgfg(argv);
        break;
    default:
        break;
    }

    return builtin;
}
```

## `do_fgbg`

需要注意的是，記得取得作業後，依對應命令修改作業的`state`。以及使用`kill`傳送信號時，應傳入`-j->pid`，帶負號`-`表示將信號傳送到`|pid|`所屬的進程組中的所有進程中。

``` C
/* 
 * do_bgfg - Execute the builtin bg and fg commands
 */
void do_bgfg(char **argv) 
{
    if (argv[1] == NULL) {
        printf("%s command requires PID or %%jobid argument\n", argv[0]);
        return;
    }

    if (isalpha(*argv[1])) {
        printf("%s: argument must be a PID or %%jobid\n", argv[0]);
        return;
    }

    /* get the job who needs to continue */
    struct job_t *j;
    char *delim = strchr(argv[1], '%');
    if (delim == NULL) {            /* use PID */
        pid_t pid = atoi(argv[1]);
        j = getjobpid(jobs, pid);

        if (j == NULL) {
            printf("(%d): No such process\n", pid);
            return;
        }
    }
    else {                          /* use JID */
        int jid = atoi(++argv[1]);
        j = getjobjid(jobs, jid);

        if (j == NULL) {
            printf("%%%s: No such job\n", argv[1]);
            return;
        }
    }

    if (strcmp(argv[0], "bg") == 0) {                /* continue in background */
        j->state = BG;
        printf("[%d] (%d) %s", j->jid, j->pid, j->cmdline);
        Kill(-j->pid, SIGCONT);
    }
    else {                                          /* continue in foreground */
        j->state = FG;
        Kill(-j->pid, SIGCONT);
        waitfg(j->pid);
    }
    return;
}
```

## `waitfg`

我們使用`sigsuspend(&mask)`掛起進程，其行為等同於以下代碼的原子(不可中斷)版本，解決了無限掛起的問題：

``` C
sigprocmask(SIG_SETMASK, &mask, &prev);
/* 若此時收到信號，可能導致進程被無限掛起 */
pause();
sigprocmask(SIG_SETMASK, &prev, NULL);
```

``` C
/* 
 * waitfg - Block until process pid is no longer the foreground process
 */
void waitfg(pid_t pid)
{
    sigset_t mask;
    Sigemptyset(&mask);
    
    while (fgpid(jobs) == pid)
        sigsuspend(&mask);

    return;
}
```

## `sigchld_handler`

需要注意，我們需要使用`while`而不是`if`來回收。這是因為必須考慮信號不會排隊的問題，若有兩個進程同時發送`SIGCHLD`信號，則只會被視為一個。如果使用`if`回收，則無法收回所有僵死進程。

還需要注意的是，處理函數可能會改變`errno`的值，所以需要在進入函數時保存舊值，並在退出時恢復。

``` C
/* 
 * sigchld_handler - The kernel sends a SIGCHLD to the shell whenever
 *     a child job terminates (becomes a zombie), or stops because it
 *     received a SIGSTOP or SIGTSTP signal. The handler reaps all
 *     available zombie children, but doesn't wait for any other
 *     currently running children to terminate.  
 */
void sigchld_handler(int sig) 
{
    int olderrno = errno;
    
    sigset_t mask, prev;
    Sigfillset(&mask);

    pid_t pid;
    int status;
    
    while ( (pid = waitpid(-1, &status, WNOHANG | WUNTRACED)) > 0) {
        Sigprocmask(SIG_BLOCK, &mask, &prev);   /* block all */
        if (WIFEXITED(status))      /* job exit */
            deletejob(jobs, pid);
        if (WIFSIGNALED(status)) {  /* job interrupt */
            printf("Job [%d] (%d) terminated by signal %d\n", pid2jid(pid), pid, WTERMSIG(status));
            deletejob(jobs, pid);
        }
        if (WIFSTOPPED(status)) {   /* job suspend */
            struct job_t *j = getjobpid(jobs, pid);
            if (j) {
                j->state = ST;
                printf("Job [%d] (%d) stopped by signal %d\n", j->jid, pid, WSTOPSIG(status));
            }
            else 
                printf("cannot find a job that corresponding to pid: %d", pid);
        }    
        Sigprocmask(SIG_SETMASK, &prev, NULL);  /* unblock all */
    }

    /* waitpid sets errno to ECHILD if there's no more zombie process */
    /* be careful: we have to ignore EINTR too */
    if (errno != ECHILD && errno != EINTR)
        unix_error("waitpid error");

    errno = olderrno;
    return;
}
```

## `sigint_handler`

不難，看看注釋。

``` C
/* 
 * sigint_handler - The kernel sends a SIGINT to the shell whenver the
 *    user types ctrl-c at the keyboard.  Catch it and send it along
 *    to the foreground job.  
 */
void sigint_handler(int sig) 
{
    int olderrno = errno;

    pid_t pid = fgpid(jobs);

    /* we don't need to response when there's no foreground job */
    if (pid == 0) {
        errno = olderrno;
        return;
    }
    
    sigset_t mask, prev;
    Sigfillset(&mask);
    
    Sigprocmask(SIG_BLOCK, &mask, &prev);   /* block all signals */

    /* send signal to all the process in the same group to pid */
    Kill(-pid, sig);

    Sigprocmask(SIG_SETMASK, &prev, NULL);  /* unblock all signals */

    errno = olderrno;
    return;
}
```

## `sigtstp_handler`

與`sigint_handler`差不多。

``` C
/*
 * sigtstp_handler - The kernel sends a SIGTSTP to the shell whenever
 *     the user types ctrl-z at the keyboard. Catch it and suspend the
 *     foreground job by sending it a SIGTSTP.  
 */
void sigtstp_handler(int sig) 
{
    int olderrno = errno;

    pid_t pid = fgpid(jobs);

    if (pid == 0) {
        errno = olderrno;
        return;
    }
    
    sigset_t mask, prev;
    Sigfillset(&mask);
    
    Sigprocmask(SIG_BLOCK, &mask, &prev);   /* block all signals */
    
    Kill(-pid, sig);
    
    Sigprocmask(SIG_SETMASK, &prev, NULL);  /* unblock all signals */

    errno = olderrno;
    return;
}
```

# 測試

使用`make`編譯程序，然後使用`make test01`，`make test02`......測試程序。

可以使用`make rtest01`運行標準解答。

對比兩份輸出可以知道程序是否運行正確。

# 後記

這個lab是寫的最順的一個，因為遇到問題實在找不到bug就直接去找chatgpt，不像之前幾個lab要動腦子不敢問gpt，怕他一不小心就把答案給出來。

關於各種`sig_handler`書中都有大差不差的代碼例子，創建子進程的邏輯書中也寫得很清楚，寫起來很順。

因為我是第一次寫並發的代碼，可能有地方寫錯或沒考慮清楚，如果各位師傅發現任何錯誤歡迎指正。