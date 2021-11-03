# grep

- 用途：查找文件內符合條件的字符串

## 語法

```shell
grep [-abcEFGhHilLnqrsvVwxy][-A<顯示行數>][-B<顯示列數>][-C<顯示列數>][-d<進行動作>][-e<範本樣式>][-f<範本文件>][--help][範本樣式][文件或目錄...]
```

## 參數

| 正規表示式選項        | 說明                                                                                                 |
| --------------------- | ---------------------------------------------------------------------------------------------------- |
| -E, --extended-regexp | 使用擴展正則表達式                                                                                   |
| -F, --fixed-strings   | 將樣式視為固定字符串的列表                                                                           |
| -G, --basic-regexp    | 將樣式視為普通的表示法來使用                                                                         |
| -P, --perl-regexp     | 將樣式視為perl的表示法來使用                                                                         |
| -e, --regexp=PATTERN  | 指定字符串做為查找文件內容的樣式                                                                     |
| -f, --file=FILE       | 指定規則文件，其內容含有一個或多個規則樣式，讓grep查找符合規則條件的文件內容，格式為每行一個規則樣式 |
| -i, --ignore-case     | 忽略大小寫的差異                                                                                     |
| -w, --word-regexp     | 只匹配整個單詞，而不是字符串的一部分                                                                 |
| -x, --line-regexp     | 只顯示全列符合的列                                                                                   |
| -z, --null-data       | 設定資料列結尾為空白位元組，非換列符號                                                               |
| -s, --no-messages     | 不顯示不存在或無匹配文本的錯誤信息                                                                   |
| -v, --invert-match    | 將匹配的資料排除                                                                                     |


| 參數                        | 說明                                                                     |
| --------------------------- | ------------------------------------------------------------------------ |
| -m, --max-count=NUM         | 在達到 NUM 符合項目後停止                                                |
| -b, --byte-offset           | 在顯示符合樣式的那一行之前，標示出該行第一個字符的編號                   |
| -n, --line-number           | 標示匹配文字的行號                                                       |
| --line-buffered             | 輸出每列後清除輸出                                                       |
| -H, --with-filename         | 印出每個符合項目的檔名                                                   |
| -h, --no-filename           | 查詢多文件時不顯示文件名                                                 |
| --label=LABEL               | 以 LABEL 作標準輸入的檔名前綴                                            |
| -o, --only-matching         | 只顯示每列中符合 PATTERN 的部分                                          |
| -q, --quiet, --silent       | 不顯示任何信息                                                           |
| --binary-files=TYPE         | 設定二進制檔案為 TYPE 的檔案;TYPE 為 "binary"、"text" 或 "without-match" |
| -a, --text                  | 不要忽略二進制的數據                                                     |
| -I                          | 不匹配二進制的東西                                                       |
| -d, --directories=ACTION    | 目錄操作的動作，讀取、遞歸、跳過                                         |
| -D, --devices=ACTION        | 設置對設備的動作，FIFO和管道的操作，動作有，讀取、跳過                   |
| -r, --recursive             | 在指定目錄與其子目錄下所有的檔案中，搜尋指定的關鍵字                     |
| -R, --dereference-recursive | 與-r相同，但遵循軟連結                                                   |
| --include=FILE_PATTERN      | 從特定的檔案中尋找關鍵字                                                 |
| --exclude=FILE_PATTERN      | 跳過匹配FILE_PATTERN 的文件和目錄                                        |
| --exclude-from=FILE         | 跳過所有除FILE 以外的文件                                                |
| --exclude-dir=PATTERN       | 跳過匹配PATTERN 的目錄                                                   |
| -L, --files-without-match   | 列出不匹配的文件名                                                       |
| -l, --files-with-matches    | 只列出匹配的文件名                                                       |
| -c, --count                 | 只輸出匹配行的計數                                                       |
| -Z, --null                  | 在搜尋的字串後面印出空字符                                               |

| 內容控制                       | 說明                                                                                                                                                                      |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -B, --before-context=NUM       | 顯示前幾行                                                                                                                                                                |
| -A, --after-context=NUM        | 顯示後幾行                                                                                                                                                                |
| -C, --context=NUM, -NUM        | 顯示前後各幾行                                                                                                                                                            |
| --group-separator=SEP          | 使用`A`、`-B`或`-C`時，在組之間打印SEP而不是--線                                                                                                                          |
| --no-group-separator           | 使用`A`、`-B`或`-C`時，在組之間不打印seperator                                                                                                                            |
| --color[=WHEN],--colour[=WHEN] | 使用顏色標示的方式，將成功匹配的部分文字標示出來，方便使用者閱讀。顏色標示功能可以透過 `--color=never`、`--color=always`、`--color=auto` 這幾種參數來關閉、開啟或設為自動 |
| -U, --binary                   | 使用標誌高亮匹配字串                                                                                                                                                      |
| -u, --unix-byte-offsets        | 使用標誌高亮匹配字串                                                                                                                                                      |

## 基本操作

## 參考資料
* http://linux.51yip.com/search/grep
* https://man7.org/linux/man-pages/man1/grep.1.html
* 
## 相關指令(可選)
