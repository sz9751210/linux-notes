# logrotate

- 用途：日誌文件管理工具，用於切割日誌，壓縮轉存，刪除舊的日誌文件，並創建新的日誌文件
- 預設配置文件位置：
```shell
/etc/logrotate.conf
/etc/logrotate.d
```
## 運行機制
logrotate是透過cron來運行的，透過/etc/cron.daily/logrotate這腳本，如要查看cron.daily運行方式，可查看/etc/anacrontab

* /etc/anacrontab
```shell
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
# the maximal random delay added to the base delay of the jobs
RANDOM_DELAY=45
# the jobs will be started during the following hours only
START_HOURS_RANGE=3-22

#period in days   delay in minutes   job-identifier   command
1	5	cron.daily		nice run-parts /etc/cron.daily
7	25	cron.weekly		nice run-parts /etc/cron.weekly
@monthly 45	cron.monthly		nice run-parts /etc/cron.monthly
```
上面可看到執行cron.daily是在凌晨3.到22.之間，並且隨機延遲45分鐘

## 語法

```shell
logrotate [OPTIONS] config_file
```

## 參數

| 選項                  | 說明                              |
| --------------------- | --------------------------------- |
| -d, --debug           | debug模式，測試配置文件是否有錯誤 |
| -f, --force           | 強制轉儲文件                      |
| -m, --mail=command    | 壓縮日誌後，發送日誌到指定郵箱    |
| -s, --state=statefile | 使用指定的狀態文件                |
| -v, --verbose         | 顯示轉儲過程                      |
| -l, --log=STRING      | log file                          |

| 設定檔參數                | 說明                                                                                                                                                           |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| compress                  | 在輪循任務完成後，已輪循的歸檔將使用 gzip 進行壓縮                                                                                                             |
| compresscmd               | 指定壓縮工具，默認為gzip                                                                                                                                       |
| uncompresscmd             | 指定解壓縮工具，默認為gunziip                                                                                                                                  |
| compressext               | 指定要在壓縮日誌文件上使用的擴展名，默認遵循配置的壓縮命令                                                                                                     |
| compressoptions           | 壓縮指令的選項配置，                                                                                                                                          |
| copy                      | 製作log檔的副本，與create互斥                                                                                                                                  |
| copytruncate              | 用於還在打開中的日誌文件，把當前日誌備份並截斷                                                                                                                 |
| create mode owner group   | 以指定的權限創建全新的日誌文件，同時 logrotate 也會重命名原始日誌文件                                                                                          |
| daily                     | 日誌文件將按天輪循                                                                                                                                             |
| dateext                   | 使用當前日期作為命名格式                                                                                                                                       |
| dateformat format_string  | 配合dateext使用，緊跟在下一行出現，定義文件切割後的文件名，必須配合dateext使用，只支持`%Y %m %d %s`這四個參數                                                  |
| delaycompress             | 和 compress 一起使用時，轉儲的日誌文件到下一次轉儲時才壓縮                                                                                                     |
| extension ext             | 維護擴展名                                                                                                                                                     |
| ifempty                   | 即使是空文件也轉儲                                                                                                                                             |
| include file_or_directory | 將logrotate格式的檔案或是目錄整個引進或                                                                                                                        |
| mail address              | 把轉儲的日誌文件發送到指定的 E-mail 地址                                                                                                                       |
| mailfirst                 | 當啟用mail參數時，寄出剛rotated的文件                                                                                                                          |
| maillast                  | 使用 mail 命令時，郵寄即將到期的文件，而不是剛剛旋轉的文件                                                                                                     |
| maxage count              | 刪除超過count天的rotated日誌                                                                                                                                   |
| minsize size              | 日誌文件在大於size字節時rotated，但不會在額外指定的時間間隔（每天、每週、每月或每年）之前輪換。使用minsize時，會同時考慮日誌文件的大小和時間戳，size選項則不會 |
| missingok                 | 在日誌輪循期間，任何錯誤將被忽略，例如"文件無法找到"之類的錯誤                                                                                                 |
| monthly                   | 日誌文件將按月輪循                                                                                                                                             |
| nocompress                | 不壓縮                                                                                                                                                         |
| nocopy                    | 不複製                                                                                                                                                         |
| nocopytruncate            | 備份日誌文件但是不截斷                                                                                                                                         |
| nocreate                  | 不建立新的日誌文件                                                                                                                                             |
| nodelaycompress           | 覆蓋 delaycompress 選項，轉儲同時壓縮                                                                                                                          |
| nodateext                 | rotate不帶日期                                                                                                                                                 |
| nomail                    | 轉儲時不發送日誌文件                                                                                                                                           |
| nomissingok               | log檔不存在會噴錯                                                                                                                                              |
| noolddir                  | 轉儲後的日誌文件和當前日誌文件放在同一個目錄下                                                                                                                 |
| nosharedscripts           | Run prerotate and postrotate scripts for every log file which is rotated                                                                                       |
| noshred                   | 刪除舊log時不要使用shred。                                                                                                                                     |
| notifempty                | 如果日誌文件為空，輪循不會進行                                                                                                                                 |
| olddir directory          | 儲後的日誌文件放入指定的目錄，必須和當前日誌文件在同一個文件系統                                                                                               |
| postrotate/endscript      | 在所有其它指令完成後，postrotate和endscript裡面指定的命令將被執行                                                                                              |
| prerotate/endscript       | 在轉儲以前需要執行的命令可以放入這個對，這兩個關鍵字必須單獨成行                                                                                               |
| firstaction/endscript     | firstaction以及endscript之間優先執行                                                                                                                           |
| lastaction/endscript      | lastaction以及endscript之間最後執行                                                                                                                            |
| rotate count              | 指定日誌文件刪除之前轉儲的次數，一次將存儲count個歸檔日誌。對於第count+1個歸檔，時間最久的歸檔將被刪除，0指沒有備份                                            |
| size size                 | 當日誌文件到達指定的大小時才轉儲                                                                                                                               |
| sharedscripts             | 運行postrotate腳本，作用是在所有日誌都輪轉後統一執行一次腳本。如果沒有配置這個，那麼每個日誌輪轉後都會執行一次腳本                                             |
| shred                     | 使用shred -u而不是unlink()刪除log文件。這應該確保log在預定刪除後不可讀                                                                                         |
| shredcycles count         | 要求 GNU shred(1) 在刪除之前覆蓋日誌文件計數次數                                                                                                               |
| start count               | This is the number to use as the base for rotation.                                                                                                            |
| tabooext [+] list         | 不轉儲指定擴展名的文件                                                                                                                                         |
| weekly                    | 日誌文件將按週輪循                                                                                                                                             |
| yearly                    | 日誌文件將按年輪循                                                                                                                                             |

## 基本操作
1. 調用/etc/logrotate.d下配置的所有日誌
```shell
logrotate /etc/logrotate.conf
```

2. 指定logrotate檔
```shell
logrotate /etc/logrotate.d/logrotate_file
```

3. 使用debug模式進行故障排除
```shell
logrotate -d /etc/logrotate.d/logrotate_file
```

4. 強制rotate
```shell
logrotate -df /etc/logrotate.d/logrotate_file
```

5. 顯示rotate過程
```shell
logrotate -v /etc/logrotate.d/logrotate_file
```

## 配置文件案例

1. syslog
```shell
/var/log/cron
/var/log/maillog
/var/log/messages
/var/log/secure
/var/log/spooler
{
    missingok
    sharedscripts
    postrotate
	/bin/kill -HUP `cat /var/run/syslogd.pid 2> /dev/null` 2> /dev/null || true
    endscript
}
```

2. jenkins
```shell
/var/log/jenkins/jenkins.log /var/log/jenkins/access_log {
    compress
    dateext
    maxage 365
    rotate 99
    size=+4096k
    notifempty
    missingok
    create 644
    copytruncate
}
```

3. nginx
```shell
/var/log/nginx/*.log /var/log/nginx/*/*.log{
	daily
	missingok
	rotate 14
	compress
	delaycompress
	notifempty
	create 640 root adm
	sharedscripts
	postrotate
		[ ! -f /var/run/nginx.pid ] || kill -USR1 `cat /var/run/nginx.pid`
	endscript
}
```

## 參考資料
* https://wsgzao.github.io/post/logrotate/
* https://linux.die.net/man/8/logrotate
* http://www.lightxue.com/how-logrotate-works
* https://www.linode.com/docs/guides/use-logrotate-to-manage-log-files/
* https://linux.cn/article-4126-1.html
* https://blog.51cto.com/luweiv998/2354160
* https://shazi.info/logrotate-%E5%9B%A0%E7%82%BA%E7%88%B6%E7%9B%AE%E9%8C%84%E6%AC%8A%E9%99%90%E8%80%8C%E5%9F%B7%E8%A1%8C%E5%A4%B1%E6%95%97/
## 相關指令(可選)
