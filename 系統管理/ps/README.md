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

## 基本操作

## 參考資料
* http://shutdown2110.blogspot.com/2018/07/linux-ps-top-cpu.html
* https://www.wongwonggoods.com/linux/linux_useful_command/linux-grep-pgrep-pid/
## 相關指令
* top
* kill
* pgrep