# ps(process status)

- 用途：顯示當前進程的狀態

## 語法

```shell
ps [OPTIONS]
```

## 參數

| 基本           | 說明                                   |
| -------------- | -------------------------------------- |
| -A, -e         | 顯示所有進程                           |
| -a             | 顯示同一終端下的所有程序               |
| a              | 顯示同一終端下的所有程序，包含其他用戶 |
| -d             | 查看除了session leaders外的所有進程    |
| -N, --deselect | 反向選擇                               |
| r              | 只列出現行終端機正在執行中的程序       |
| T              | 顯示當前終端的所有程序                 |
| x              | 顯示所有程序，不以終端機來區分         |

| 分類                                    | 說明                  |
| --------------------------------------- | --------------------- |
| -C \<command>                           | 透過指定的命令分類    |
| -G, --Group \<group_name>               | 透過group名稱分類     |
| -g, --group \<group_id>                 | 透過group id分類      |
| -p, p, --pid \<PID>                     | 透過pid分類           |
| --ppid \<PID>                           | 透過ppid分類          |
| -q, q, --quick-pid \<PID>               | 透過pid分類(快速模式) |
| -s, --sid \<session>                    | 透過session id分類    |
| -t, t, --tty \<tty>                     | 透過指定tty分類       |
| -u, -U, U, --User \<UID>, --user \<UID> | 指定用戶的所有進程    |


| 輸出格式                         | 說明                                                |
| -------------------------------- | --------------------------------------------------- |
| -F                               | 比`-f`多顯示SZ,RSS,PSR,STIME欄位                    |
| -f                               | 顯示UID,PPIP,C與TIME欄位                            |
| f, --forest                      | 顯示程序間的關係                                    |
| -H                               | 精簡版`f`                                           |
| -j, j                            | 採用工作控制的格式顯示進程狀況                      |
| -l, l                            | 採用詳細的格式來顯示進程狀況                        |
| -M, Z                            | add security data (for SELinux)                     |
| -O \<format>, O \<format>        | preloaded with default columns                      |
| -o, o, --format \<format>        | 自定義格式                                          |
| s                                | 採用程序信號的格式(signal format)顯示程序狀況       |
| u                                | 以用戶為主的格式來顯示程序狀況                      |
| v                                | 採用虛擬內存的格式顯示程序狀況                      |
| X                                | 採用舊式的Linux i386登陸格式顯示程序狀況            |
| -y                               | do not show flags, show rss vs. addr (used with -l) |
| --context                        | display security context (for SELinux)              |
| --headers                        | 重複顯示標題列                                      |
| --no-headers                     | 不顯示標題列                                        |
| --cols, --columns, --width <num> | 設置每列的最大字符數                                |
| --rows, --lines <num>            | 設置顯示畫面的列數                                  |


| 顯示執行緒 | 說明                                   |
| ---------- | -------------------------------------- |
| H          | Show threads as if they were processes |
| -L         | 顯示線程，可能帶有 LWP 和 NLWP 列      |
| -m, m      | 在進程之後顯示線程                     |
| -T         | 顯示線程，可能帶有 SPID 列             |

| 其他               | 說明                                                                       |
| ------------------ | -------------------------------------------------------------------------- |
| -c                 | 顯示CLS和PRI欄位                                                           |
| c                  | 列出進程時，顯示每個進程真正的指令名稱，而不包含路徑，參數或常駐服務的標示 |
| e                  | 列出進程時，顯示每個進程所使用的環境變量                                   |
| k,    --sort       | 依照指定欄位做排序                                                         |
| L                  | 列出欄位的相關信息                                                         |
| n                  | 以數字來表示USER和WCHAN欄位                                                |
| S,    --cumulative | 列出進程時，包括已中斷的子進程資料                                         |
| -y                 | 配合參數`-l`使用時，不顯示F(flag)欄位，並以RSS欄位取代ADDR欄位             |
| -w, w              | 採用寬闊的格式來顯示進程狀況                                               |

| 輸出格式 | 說明                 |
| -------- | -------------------- |
| USER     | 行程擁有者           |
| PID      | pid                  |
| %CPU     | 佔用的CPU使用率      |
| %MEM     | 佔用的MEM使用率      |
| VSZ      | 佔用的虛擬記憶體大小 |
| RSS      | 佔用的記憶體大小     |
| TTY      | 終端的次要裝置號碼   |
| STAT     | 該行程的狀態         |
| START    | 行程開始的時間       |
| TIME     | 執行的時間           |
| COMMAND  | 執行的指令           |

ps工具標識進程的5種狀態碼: 
| 狀態碼 | 說明 |
| ---- | ---- |
|   D   |  不可中斷 uninterruptible sleep (usually IO)     |
|  R    |  運行 runnable (on run queue)     |
|   S   |   中斷 sleeping    |
|  T    |  停止 traced or stopped     |
|  Z    | 僵死 a defunct (」zombie」) process      |
|      |      |
|      |      |
|      |      |

>linux上進程有5種狀態: 
>1. 運行(正在運行或在運行隊列中等待) 
>2. 中斷(休眠中, 受阻, 在等待某個條件的形成或接受到信號) 
>3. 不可中斷(收到信號不喚醒和不可運行, 進程必須等待直到有中斷髮生) 
>4. 僵死(進程已終止, 但進程描述符存在, 直到父進程調用wait4()系統調用後釋放) 
>5. 停止(進程收到SIGSTOP, SIGSTP, SIGTIN, SIGTOU信號後停止運行運行) 

## 基本操作
1. 顯示所有進程信息
```shell
ps -A or ps -e

# 如果要帶命令行 可再添加-f參數
ps -ef
```

2. 不區分終端，顯示所有用戶的所有進程
```shell
ps aux
```


3. 顯示指定用戶訊息
```shell
# 查看root用戶的進程信息
ps -u root
```

4. 查找特定進程
```shell
# 查找ssh進程
ps -ef | grep ssh
```

5. 依據輸出欄位做排序
```shell
# 依據CPU使用率列出前五名
ps aux --sort -pcpu | head -5 or ps au --sort -pcpu | head -5

# 依據MEM使用率列出前五名
ps aux --sort -pmem | head -5 or ps au --sort -pmem | head -5
```
> 透過[-,+]pcpu,pmem等欄位來實現降序或是升序

6. 自定義輸出格式
```shell
# 依照cpu使用率升序排序指定欄位
ps axo pid,comm,pcpu --sort +cpu
```

7. 重新定義欄位名稱
```shell
ps -e -o pid,uname=USERNAME,pcpu=CPU_USAGE,pmem,comm
```

8. 查看進程並按內存使用大小排序
```shell
ps -e -o "%C : %p :%z : %a"|sort -k5 -nr
```

9. 用樹狀的風格顯示進程的層次關係
```shell
ps auf
```

## 參考資料
* http://shutdown2110.blogspot.com/2018/07/linux-ps-top-cpu.html
* https://www.wongwonggoods.com/linux/linux_useful_command/linux-grep-pgrep-pid/
* https://www.networkworld.com/article/3596800/how-to-sort-ps-output.html
* http://linux.51yip.com/search/ps
* https://www.geeksforgeeks.org/ps-command-in-linux-with-examples/
* https://kknews.cc/zh-tw/code/4pnr3o2.html
## 相關指令
* top
* kill
* pgrep