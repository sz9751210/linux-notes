# cp(copy)

- 用途：複製檔案和目錄

## 語法

```shell
cp [OPTIONS] SOURCE DEST
```

## 參數

| 參數                        | 說明                                                                                                                                                                    |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -a, --archive               | 效果同`-dpR`，保留連結、文件屬性，並複製目錄下的所有內容，通常在複製目錄時使用                                                                                          |
| --attributes-only           | 只複製文件的屬性，內容不複製                                                                                                                                            |
| --backup[=CONTROL]          | 備份每個現有的目標文件                                                                                                                                                  |
| -b                          | 不接受參數版的--backup                                                                                                                                                  |
| --copy-contents             | 遞歸模式下複製特殊文件的內容                                                                                                                                            |
| -d                          | 複製時保留軟連結                                                                                                                                                        |
| -f, --force                 | 強制覆蓋已經存在的目標文件，不會跳出提示                                                                                                                                |
| -i, --interactive           | 與`-f`選項相反，在覆蓋目標文件之前給出提示，要求用戶確認是否覆蓋，回答 y 時目標文件將被覆蓋。                                                                           |
| -H                          | 跟隨源文件命令行中顯式給出的符號鏈接                                                                                                                                    |
| -l, --link                  | 使用硬鏈接取代複製                                                                                                                                                      |
| -L, --dereference           | 總是跟隨源文件中的符號鏈接                                                                                                                                              |
| -n, --no-clobber            | 不要覆寫已有的文件（覆蓋先前給出的 -i 選項）                                                                                                                            |
| -P, --no-dereference        | 永遠不要跟隨源文件中的符號鏈接                                                                                                                                          |
| -p                          | 不接受參數版的--preserve                                                                                                                                                |
| --preserve[=ATTR_LIST]      | 除複製文件的內容外，還把修改時間和訪問權限也複製到新文件中。保留指定的屬性（默認：模式、從屬關係、時間戳），如果可能的話還有額外屬性：上下文、鏈接（links）、xattr、all |
| --no-preserve=ATTR_LIST     | 不要保留指定的屬性                                                                                                                                                      |
| --parents                   | 在目標目錄下使用完整的源文件名                                                                                                                                          |
| -R, -r, --recursive         | 遞歸複製目錄                                                                                                                                                            |
| --reflink[=WHEN]            | 控制克隆/寫入時複製（CoW）副本。詳情見下文                                                                                                                              |
| --remove-destination        | 打開目的                                                                                                                                                                |
| --sparse=WHEN               | 控制稀疏文件的創建。詳情見下文                                                                                                                                          |
| --strip-trailing-slashes    | 移除每個源文件參數後的任何末尾斜槓                                                                                                                                      |
| -s, --symbolic-link         | 建立軟連結而不是複制                                                                                                                                                    |
| -S, --suffix=後置字串       | 覆蓋原本的備份後綴                                                                                                                                                      |
| -t, --target-directory=目錄 | 將所有源文件參數給出的內容複製到目標目錄中                                                                                                                              |
| -T, --no-target-directory   | 將目標文件當作普通文件對待（而不是目錄）                                                                                                                                |
| -u, --update                | 僅在源文件比目標文件新，或者目標文件不存在的情況下複製                                                                                                                  |
| -v, --verbose               | 顯示覆蓋訊息                                                                                                                                                            |
| -x, --one-file-system       | 停留在當前文件系統中                                                                                                                                                    |
| -Z                          | 將目標文件的 SELinux 安全上下文設置為默認類型                                                                                                                           |
| --context[=CTX]             | 類似`-Z`，或者如果給定了上下文（CTX）那麼將SELinux或者SMACK                                                                                                             |
| 安全上下文設置爲給定值      |

默認情況下，程序會使用一種粗糙的啓發式算法探測源文件是否是稀疏的，若判定爲稀疏，則目標文件也會以稀疏形式創建。這個行爲可以通過
* `--sparse=auto`指定。若指定
* `--sparse=always`，將在源文件包含足夠多內容爲零的字節序列時將其視作稀疏文件。使用
* `--sparse=never` 以禁止創建稀疏文件。

當指定了`--reflink[=always]`時，進行輕量級複製，其中的數據塊僅在被修改時進行復制。如果這樣的複製失敗，或無法實行，或者指定了`--reflink=auto`時，回退到標準複製。

備份的後綴爲`"~"`，除非設置了`--suffix`或者`SIMPLE_BACKUP_SUFFIX`。版本控制方式可以使用
`--backup`選項或者`VERSION_CONTROL`環境變量進行指定。可用的值如下：
* none, off：永遠不製作備份（即使給出了 --backup ）
* numbered, t：製作編號的備份
* existing, nil：如果已編號副本存在則編號，否則採用簡單方式
* simple, never：總是製作簡單備份
作爲一個特例，`cp`將在同時給出`force`選項與`backup`選項，並且源文件和目標文件是同一個已存在普通文件的情況下製作備份副本。

## 基本操作
1. 複製目錄
```shell
cp -r source/ destdir
```
2. 複製並改名
```shell
cp aaa bbb
```
3. 複製目錄及屬性
```shell
cp -rp source/ destdir
```
4. 複製多檔到單目錄下
```shell
cp aaa bbb destdir
```
5. 透過匹配複製
```shell
cp *.log dest
```

## 參考資料
* [Ubuntu Manpage: cp - 複製文件和目錄](http://manpages.ubuntu.com/manpages/bionic/zh_TW/man1/cp.1.html)
* [Linux cp 指令用法 (link.idv.tw)](http://www.link.idv.tw/linux_command_file/Linux_cp_command.htm)
* [Linux cp Command Examples (linuxhint.com)](https://linuxhint.com/cp-command-linux/)