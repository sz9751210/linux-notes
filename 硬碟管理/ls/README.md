# ls(list files)

- 用途：顯示目錄中的檔案與目錄列表

## 語法

```shell
ls [OPTIONS] dirname
```

## 參數

| 參數                                      | 說明                                                                       |
| ----------------------------------------- | -------------------------------------------------------------------------- |
| -a, --all                                 | 顯示所有文件和目錄，包含.開頭的隱藏檔案。                                  |
| -A, --almost-all                          | 顯示所有文件和目錄，包含.開頭的隱藏檔案，但不顯示當前目錄和上層目錄(.和..) |
| --author                                  | 搭配-l，在每個檔案顯示作者(owner, group, author)                           |
| -b, --escape                              | 顯示跳脫字元。                                                             |
| --block-size=SIZE                         | 指定顯示的文件和目錄單位                                                   |
| -B, --ignore-backups                      | 忽略備份的文件及目錄。                                                     |
| -c                                        | 以更改時間排序，                                                           |
| -C                                        | 以由上到下，從左到右的直行方式顯示                                         |
| --color[=WHEN]                            | 調整檔案輸出時是否要加上顏色                                               |
| -d, --directory                           | 列出目錄，其餘不顯示。                                                     |
| -D, --dired                               | 用Emacs的模式產生文件和目錄列表。                                          |
| -f                                        | 此參數的效果和同時指定`-aU`參數相同，並關閉`-lst`參數的效果。              |
| -F, --classify                            | 在檔案名稱後面加上類型標示字元。                                           |
| -p, --file-type                           | 此參數的效果和指定`-F`參數類似，但不會在執行文件名稱後面加上`*`號。        |
| --format=WORD                             | 更改預設檔案輸出的排版方式                                                 |
| --full-time                               | 與 -l --time-style=full-iso一樣，                                          |
| -g                                        | 與-l類似，但只顯示群組名稱(group)，不顯示擁有者名稱。                      |
| --group-directories-first                 | 群組資料夾優先排序                                                         |
| -G, --no-group                            | 不顯示群組名稱。                                                           |
| -h, --human-readable                      | 檔案大小將轉為易讀取的形式。                                               |
| --si                                      | 與-h類似，但是-H是以1000進位而-h是以1024進位。                             |
| -H, --dereference-command-line            |                                                                            |
| --dereference-command-line-symlink-to-dir |                                                                            |
| --hide=PATTERN                            | 不列出與PATTERN匹配的文件或目錄(會被`-a`或`-A`覆蓋）                       |
| --indicator-style=WORD                    | 將帶有 WORD 樣式的指示符附加到項目名稱                                     |
| -i, --inode                               | 列出每個檔案的索引節點。                                                   |
| -I, --ignore=PATTERN                      | 不列出與PATTERN 匹配的文件或目錄                                           |
| -k, --kibibytes                           | 此參數的效果和指定`block-size=1024`參數相同。                              |
| -l                                        | 列出檔案的詳細資訊。                                                       |
| -L, --dereference                         | 當顯示軟連結的文件信息時，顯示連結引用的文件的信息。                       |
| -m                                        | 將每個檔案緊密排列，並使用逗號隔開。                                       |
| -n, --numeric-uid-gid                     | 跟-l很像，但顯示使用者的UID與群組的GID值。                                 |
| -N, --literal                             | 列出文件和目錄的名稱，包含控制字元。                                       |
| -o                                        | 與-l類似，但只顯示擁有者名稱(owner)，不顯示群組名稱。                      |
| -q, --hide-control-chars                  | 用`?`號取代控製字符，列出文件和目錄名稱。                                  |
| --show-control-chars                      | 按原樣顯示非圖形字符                                                       |
| -Q, --quote-name                          | 將文件及目錄名稱用雙引號標示起來。                                         |
| --quoting-style=WORD                      | 對文件及目錄名稱使用樣式                                                   |
| -r, --reverse                             | 將檔案以反向的順序排列。                                                   |
| -R, --recursive                           | 以遞迴的方式列出所有子目錄的檔案。                                         |
| -s, --size                                | 列出檔案的大小。(in blocks)                                                |
| -S                                        | 按照檔案大小來做排序。                                                     |
| --sort=WORD                               | 可以用來指定檔案的排序方式                                                 |
| --time=WORD                               | 更改使用時間的默認值                                                       |
| --time-style=STYLE                        | 允許使用者自訂輸出的時間格式                                               |
| -t                                        | 按照最後一次修改時間來做排序，最新的第一。                                 |
| -T, --tabsize=COLS                        |                                                                            |
| -u                                        | 按照最後一次存取時間來做排序。                                             |
| -U                                        | 按照資料夾裡的順序逐一列出，不做排序。                                     |
| -v                                        | 按照版本來做排序。                                                         |
| -w, --width=COLS                          | 指定輸出的版面寬度，設置每列的最大字元數。                                 |
| -x                                        | 以從左到右，由上至下的橫列方式顯示                                         |
| -X                                        | 按照檔案的副檔名來做排序。                                                 |
| -1                                        | 每個檔案使用一列的方式逐一列出。                                           |
## 基本操作