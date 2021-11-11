# logrotate

- 用途：日誌滾動打包
- 預設conf檔位置：`/etc/logrotate.conf`

## 原理及運行機制
### 原理
### 運行機制
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
| -l, --log=STRING      |                                   |

| 設定檔參數                | 說明                                                                                                                |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| compress                  | 在輪循任務完成後，已輪循的歸檔將使用 gzip 進行壓縮                                                                  |
| compresscmd               |                                                                                                                     |
| uncompresscmd             |                                                                                                                     |
| compressext               |                                                                                                                     |
| compressoptions           |                                                                                                                     |
| copy                      |                                                                                                                     |
| copytruncate              | 用於還在打開中的日誌文件，把當前日誌備份並截斷                                                                      |
| create mode owner group   | 以指定的權限創建全新的日誌文件，同時 logrotate 也會重命名原始日誌文件                                               |
| daily                     | 日誌文件將按天輪循                                                                                                  |
| dateext                   | 使用當前日期作為命名格式                                                                                            |
| dateformat format_string  | 配合dateext使用，緊跟在下一行出現，定義文件切割後的文件名，必須配合dateext使用，只支持`%Y %m %d %s`這四個參數       |
| delaycompress             | 和 compress 一起使用時，轉儲的日誌文件到下一次轉儲時才壓縮                                                          |
| extension ext             |                                                                                                                     |
| ifempty                   | 即使是空文件也轉儲                                                                                                  |
| include file_or_directory | 將logrotate格式的檔案或是目錄整個引進或                                                                             |
| mail address              | 把轉儲的日誌文件發送到指定的 E-mail 地址                                                                            |
| mailfirst                 |                                                                                                                     |
| maillast                  |                                                                                                                     |
| maxage count              |                                                                                                                     |
| minsize size              |                                                                                                                     |
| missingok                 | 在日誌輪循期間，任何錯誤將被忽略，例如"文件無法找到"之類的錯誤                                                      |
| monthly                   | 日誌文件將按月輪循                                                                                                  |
| nocompress                | 不壓縮                                                                                                              |
| nocopy                    |                                                                                                                     |
| nocopytruncate            | 備份日誌文件但是不截斷                                                                                              |
| nocreate                  | 不建立新的日誌文件                                                                                                  |
| nodelaycompress           | 覆蓋 delaycompress 選項，轉儲同時壓縮                                                                               |
| nodateext                 |                                                                                                                     |
| nomail                    | 轉儲時不發送日誌文件                                                                                                |
| nomissingok               |                                                                                                                     |
| noolddir                  | 轉儲後的日誌文件和當前日誌文件放在同一個目錄下                                                                      |
| nosharedscripts           |                                                                                                                     |
| noshred                   |                                                                                                                     |
| notifempty                | 如果日誌文件為空，輪循不會進行                                                                                      |
| olddir directory          | 儲後的日誌文件放入指定的目錄，必須和當前日誌文件在同一個文件系統                                                    |
| postrotate/endscript      | 在所有其它指令完成後，postrotate和endscript裡面指定的命令將被執行                                                   |
| prerotate/endscript       | 在轉儲以前需要執行的命令可以放入這個對，這兩個關鍵字必須單獨成行                                                    |
| firstaction/endscript     |                                                                                                                     |
| lastaction/endscript      |                                                                                                                     |
| rotate count              | 指定日誌文件刪除之前轉儲的次數，一次將存儲count個歸檔日誌。對於第count+1個歸檔，時間最久的歸檔將被刪除，0指沒有備份 |
| size size                 | 當日誌文件到達指定的大小時才轉儲                                                                                    |
| sharedscripts             | 運行postrotate腳本，作用是在所有日誌都輪轉後統一執行一次腳本。如果沒有配置這個，那麼每個日誌輪轉後都會執行一次腳本  |
| shred                     |                                                                                                                     |
| shredcycles count         |                                                                                                                     |
| start count               |                                                                                                                     |
| tabooext [+] list         | 不轉儲指定擴展名的文件                                                                                              |
| weekly                    | 日誌文件將按週輪循                                                                                                  |
| yearly                    | 日誌文件將按年輪循                                                                                                  |

## 基本操作

## 參考資料
* https://linux.die.net/man/8/logrotate
* http://www.lightxue.com/how-logrotate-works
* https://www.linode.com/docs/guides/use-logrotate-to-manage-log-files/
* https://linux.cn/article-4126-1.html
* https://blog.51cto.com/luweiv998/2354160
## 相關指令(可選)
