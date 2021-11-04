# timedatectl

- 用途：修改系統時間

## 語法

```shell
timedatectl [OPTIONS] command
```

## 參數

| 參數                   | 說明                                                                                                                          |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| --no-pager             | 不將程序的輸出內容管道(pipe)給分頁程序                                                                                        |
| --no-ask-password      | 在執行特權操作時不向用戶索要密碼。                                                                                            |
| -H --host=[USER@]HOST  | 操作指定的遠程主機                                                                                                            |
| -M --machine=CONTAINER | 在本地容器內執行操作。 必須明確指定容器的名稱。                                                                               |
| --adjust-system-clock  | 當使用`set-local-rtc`命令時，若使用了此選項，則表示根據RTC時間來更新系統時鐘。若未使用此選項，則表示根據系統時鐘來更新RTC時間 |


## 指令

| 指令               | 說明                                                                                                                                                         |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| status             | 顯示系統時鐘與RTC的當前狀態， 包括時區設置與網絡時間同步服務的狀態。                                                                                         |
| set-time TIME      | 將系統時鐘設爲指定的時間， 並同時更新RTC時間。 [TIME] 是一個形如 "2012-10-30 18:17:16"的時間字符串。                                                         |
| set-timezone ZONE  | 設置系統時區，也就是更新 /etc/localtime 軟連接的指向。 可以用下面的 list-timezones命令列出所有可用時區。 如果RTC被設爲本地時間， 此命令還會同時更新RTC時間。 |
| list-timezones     | 列出所有可用時區，每行一個。 列出的值可以用作前述 set-timezone 命令的參數。                                                                                  |
| set-local-rtc BOOL | 設爲 "no" 表示在RTC中存儲UTC時間； 設爲 "yes" 表示在RTC中存儲本地時間。應該盡一切可能在RTC中存儲UTC時間                                                      |
| set-ntp BOOL       | 是否開啓網絡時間同步。 設爲 "yes" 則啓用並啓動 systemd-timesyncd.service 服務， 設爲"no" 則停止並停用它                                                      |


## 基本操作
1. 顯示當前系統時間
```shell
timedatectl or timedatectl status
```

2. 開啟網路時間同步服務
```shell
timedatectl set-ntp true
```

3. 設定日期與時間
```shell
# 改時間和日期
timedatectl set-time "2021-11-01 10:10:00"

# 只改日期
timedatectl set-time "2021-11-01"
timedatectl set-time 20211101

# 只改時間
timedatectl set-time "10:10:00"
timedatectl set-time 10:10:00
```

4. 檢查時區
```shell
timedatectl list-timezones

# 根據地理位置查看時區
timedatectl list-timezones | grep "Asia/B.*"
```


5. 設定時區
```shell
timedatectl set-timezone "Asia/Taipei"

# 設定為世界協調時間(UTC)
timedatectl set-timezone UTC
```


## 參考資料
* http://manpages.ubuntu.com/manpages/bionic/zh_TW/man1/timedatectl.1.html
* https://blog.gtwang.org/linux/howto-set-date-time-from-linux-command-prompt/
* https://www.gushiciku.cn/pl/gxVn/zh-tw

## 相關指令
* date
* hwclock