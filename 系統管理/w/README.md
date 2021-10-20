# w

- 用途：顯示目前登入系統的使用者相關資訊，透過這指令可得知目前登入系統的使用者有誰，登入系統人數與系統已啟動時間，以及他們正在下什麼指令。

## 語法

```shell
w [OPTIONS][用戶名稱]
```

## 參數

| 參數            | 說明                                                                        |
| --------------- | --------------------------------------------------------------------------- |
| -f,--from       | 開啟或關閉顯示用戶從何處登入系統                                            |
| -h,--no-header  | 不顯示個欄位的標題訊息列                                                    |
| -u,--no-current | 忽略執行程序的名稱，以及該程序耗費CPU時間的信息。                           |
| -s,--short      | 使用簡潔格式列表，不顯示用戶登入時間，終端機階段作業和程序所耗費的CPU時間。 |
| -i,--ip-addr    | 顯示ip地址而不是主機名                                                      |
| -o,--old-style  | 舊版輸出，JCPU以及PCPU不顯示，IDLE小於1分鐘不顯示                           |
|                 |                                                                             |

## 欄位介紹

| 欄位   | 說明                                                 |
| ------ | ---------------------------------------------------- |
| USER   | 登入的使用者                                         |
| TTY    | 表示終端機                                           |
| FROM   | 表示來源位址                                         |
| LOGIN@ | 表登入時間                                           |
| IDLE   | 表閒置時間                                           |
| JCPU   | 表示對於同一個終端機下所有程序累績的執行時間         |
| PCPU   | 表示 WHAT 欄位所顯示的程序所顯示的程序累積的執行時間 |
| WHAT   | 表示目前正執行的工作                                 |

```shell
 02:13:15(當前時間) up 38 min(系統運作時間),  2 users(當前使用者數量),  load average: 0.00, 0.03, 0.05(過去 1、5 和 15 分鐘的系統負載平均值)
USER     TTY      FROM    LOGIN@   IDLE   JCPU   PCPU WHAT
```
## 基本操作
1. 查看所有使用者登入的詳細訊息
```shell
w

# output
 02:20:24 up 45 min,  2 users,  load average: 0.01, 0.02, 0.05
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     pts/2    192.168.56.1     01:51   11:20   0.01s  0.01s -bash
alan     pts/3    192.168.56.1     01:51    0.00s  0.08s  0.00s w
```

2. 查看某位使用者alan的詳細訊息
```shell
w alan

# output
 02:20:42 up 46 min,  2 users,  load average: 0.01, 0.02, 0.05
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
alan     pts/3    192.168.56.1     01:51    2.00s  0.08s  0.00s w alan
```
3. 不顯示標題訊息列
```shell
w -h

# output
alan     pts/3    192.168.56.1     01:51    7.00s  0.08s  0.00s w -h
```
