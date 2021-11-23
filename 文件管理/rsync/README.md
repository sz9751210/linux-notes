# rsync

- 用途：用來複製與備份檔案的工具，它可以處理本機或遠端的檔案同步工作

## 語法

```shell
rsync [OPTIONS] src [dest/user@host:dest]
```

## 參數

| 參數                  | 說明                                                                                                              |
| --------------------- | ----------------------------------------------------------------------------------------------------------------- |
| -v, --verbose         | verbose 模式，輸出比較詳細的訊息                                                                                  |
| -r, --recursive       | 遞迴（recursive）備份所有子目錄下的目錄與檔案                                                                     |
| -a, --archive         | 封裝備份模式，相當於 -rlptgoD，遞迴備份所有子目錄下的目錄與檔案，保留連結檔、檔案的擁有者、群組、權限以及時間戳記 |
| -z, --compress        | 啟用壓縮，可減少網路傳輸資料量                                                                                    |
| -h, --human-readable  | 將數字以比較容易閱讀的格式輸出                                                                                    |
| -q, –quiet            | 與 -v 相反，安靜模式，略過正常資訊，僅顯示錯誤訊息                                                                |
| -l, –links            | 複製連結而不是連結內容                                                                                            |
| -g, –group            | 保留檔案的原始群組狀態(權限不足則無法繼承)                                                                        |
| -o, –owner            | 保留檔案的原始擁有者(權限不足則無法繼承)                                                                          |
| -t,–times             | 保留檔案的原始時間參數                                                                                            |
| -e                    | 使用的通道協定，例如使用 ssh 通道，則 -e ssh                                                                      |
| -u, --update          | 在備份時會略過所有已經存在於目的端，且文件時間比要備份的檔案為新的檔案                                            |
| -p, --perms           | 表示要保留檔案的權限資訊                                                                                          |
| -D                    | 表示要保留設備檔案資訊                                                                                            |
| --delete              | 刪除來源端已經不存在但在目的端存在的檔案                                                                          |
| --force               | 當目的端的目錄被覆蓋時，就強制先刪除該目錄                                                                        |
| --bwlimit=RATE        | 限制資料傳輸速度上限                                                                                              |  |
| --progress            | 即時顯示傳輸進度                                                                                                  |  |
| --exclude=PATTERN     | 排除符合匹配的檔案                                                                                                |  |
| --include=PATTERN     | 只備份符合匹配的檔案                                                                                              |  |
| --min-size=SIZE       | 指定備份檔案的最小值                                                                                              |  |
| --max-size=SIZE       | 指定備份檔案的最大值                                                                                              |  |
| --remove-source-files | 自動刪除來源檔案                                                                                                  |  |
| -n, --dry-run         | debug模式，測試rsync餐數                                                                                          |  |
| --existing            | 只更新既有的檔案，排除新增的檔案                                                                                  |  |
| -i, --itemize-changes | 查看個別檔案的變動資訊                                                                                            |  |

## 基本操作
1. 複製本地端檔案或目錄
```shell
rsync -avh mylog.log /local/path/

rsync -avh /mypath /home/alan/
```

2. 本地備份至遠端，將本地myfile.gz備份到遠端/remote/path/目錄下
```shell
rsync -avzh ./myfile.gz host@ip:/remote/path/
```

3. 遠端備份至本地
```shell
rsync -avzh host@ip:/remote/path/myfile.gz /local/path
```

4. 限制網速
```shell
rsync -avzh --bwlimit=100k host@ip:/remote/path/myfile.gz /local/path
```

5. 顯示傳輸進度
```shell
rsync -avzh --progress host@ip:/remote/path/myfile.gz /local/path
```

6. 同步刪除目的端檔案
```shell
rsync -avzh --delete host@ip:/remote/path/myfile.gz /local/path
```

7. 備份特定檔案
```shell
# 排除掉結尾為.txt的檔案
rsync -avh --exclude '*.txt' src/path dest/path

# 只備份結尾為.txt的檔案
rsync -avh --include '*.txt' src/path dest/path
```

8. 限制檔案大小
```shell
# 只備份1mb以上的檔案
rsync -avh --min-size=1m src/path dest/path

# 只備份最大1k的檔案
rsync -avh --max-size=1k src/path dest/path

# 只備份1k以上1mb以下的檔案
rsync -avh --min-size=1k --max-size=1m src/path dest/path
```

9. 自動刪除來源檔案
```shell
# 將src/path的檔案備份到dest/path後清空，相當於mv的效果
rsync -avh --remove-source-files src/path dest/path
```

10, 測試rsync參數
```shell
rsync -avh --dry-run src/path dest/path
```

11. 搭配crontab做定期備份
```crontab
# m h  dom mon dow   command
0 5 * * 1 rsync -a /path/to/folder /path/to/backup/
```

12. 只更新已存在的檔案
```shell
rsync -avh --existing src/path dest/path
```

## 參考資料
* [Rsync Command in Linux with Examples | Linuxize](https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/)
* [Linux 使用 rsync 遠端檔案同步與備份工具教學與範例 - G. T. Wang (gtwang.org)](https://blog.gtwang.org/linux/rsync-local-remote-file-synchronization-commands/)
* [Linux下如何使用Rsync備份伺服器重要資料 | IT人 (iter01.com)](https://iter01.com/608128.html)
## 相關指令
* scp