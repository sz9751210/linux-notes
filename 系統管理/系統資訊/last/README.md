# last

- 用途：列出目前與過去登入系統的使用者相關資訊

## 語法

```shell
last [OPTIONS] [num,time,name,tty]
```

## 參數

| 參數                     | 說明                                    |
| ------------------------ | --------------------------------------- |
| -f file                  | 指定登入的日誌檔案(預設是/var/log/wtmp) |
| -num                     | 指定last顯示幾行資訊                    |
| -n num                   | 與`-num`相同                            |
| -t  time[YYYYMMDDHHMMSS] | 顯示指定時間的登入資訊                  |
| -R                       | 不顯示主機名                            |
| -a                       | 在最後一列顯示主機名                    |
| -d                       | 將非本地登入的使用者ip轉換成主機名      |
| -F                       | 顯示所有的登入和登出時間和日期          |
| -i                       | 顯示ip地址而不是主機名                  |
| -o                       | 讀取舊的日誌檔案                        |
| -w                       | 顯示使用者名稱和域名                    |
| -x                       | 顯示系統關機資訊和執行級別的變化資訊    |


## 欄位說明
```shell
last

# output
1        2            3                4                  5      
alan     pts/2        192.168.56.1     Mon Oct 25 21:37   still logged in
reboot   system boot  3.10.0-1160.42.2 Mon Oct 25 21:16 - 22:39  (01:22)
alan     pts/0        192.168.56.1     Sun Oct 24 23:18 - 05:47  (06:28)
reboot   system boot  3.10.0-1160.42.2 Sun Oct 24 23:15 - 22:39  (23:24)
alan     pts/2        192.168.56.1     Fri Oct 22 02:07 - 05:44  (03:37)
```
| 欄位     | 說明                                                                                                                        |
| -------- | --------------------------------------------------------------------------------------------------------------------------- |
| 登入用戶 | 顯示登錄用戶的姓名                                                                                                          |
| 登入終端 | 顯示用戶如何連接到系統，但如果是重啟進入，則是會顯示system boot                                                             |
| 登入主機 | 顯示從哪連接到系統，欄位可為主機名或是IP位址(遠端)、空值(tty)、kernel版本(重啟)、應用程序(PID.windowID)                     |
| 登入時間 | 顯示用戶登入的時間                                                                                                          |
| 登出時間 | 顯示用戶登出的時間，欄位可為時間戳(登出)、still running(開機)、still logged in(用戶登入中)、down(機器關機)、crash(系統崩潰) |
## 基本操作
1. 顯示最近登入的5筆資訊
```shell
last -5 or last -n 5
```

2. 顯示用戶在某時段登入的資訊
```shell
last -t 20211026151111 root
```

3. 顯示終端tty1的登入資訊
```shell
last 1 or last tty1
```
## 參考資料
* [Linux last Command | Baeldung on Linux](https://www.baeldung.com/linux/last-command)
* [Linux基礎命令—last | IT人 (iter01.com)](https://iter01.com/255176.html)
