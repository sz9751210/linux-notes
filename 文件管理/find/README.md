# find

- 用途：在目錄中找尋文件

## 語法

```shell
find path [OPTIONS]
```

## 參數(常用)

| 參數                    | 說明                                                                   |
| ----------------------- | ---------------------------------------------------------------------- |
| -mount, -xdev           | 只檢查和指定目錄在同一個文件系統下的文件，避免列出其它文件系統中的文件 |
| -amin n                 | 指定檔案的最後存取時間，單位為分鐘，在過去n分鐘內被存取過              |
| -anewer file            | 比文件file更晚被存取過的文件                                           |
| -atime n                | 指定檔案的最後存取時間（access time），單位為天                        |
| -cmin n                 | 指定檔案狀態相關資訊最後修改的時間，單位為分鐘                         |
| -cnewer file            | 比文件file更新的文件                                                   |
| -ctime n                | 指定檔案狀態相關資訊最後修改的時間（status time），單位為天            |
| -mtime n                | 指定檔案的最後修改時間（modification time），單位為天                  |
| -mmin n                 | 指定檔案的最後修改時間，單位為分鐘                                     |
| -empty                  | 搜尋空檔案                                                             |
| -ipath p, -path p       | 路徑名稱符合 p 的文件，ipath 會忽略大小寫                              |
| -name name, -iname name | 文件名稱符合 name 的文件。 iname 會忽略大小寫                          |
| -size n                 | 指定檔案的大小                                                         |
| -type c                 | 指定檔案的類型                                                         |
| -perm                   | 指定檔案的權限                                                         |
| -user                   | 指定檔案擁有者                                                         |
| -group                  | 指定檔案的群組                                                         |
## 基本操作
1. 指定檔名搜尋
```shell
# 搜尋在當前目錄底下，檔名為file.txt的檔案
find . -name file.txt

# 透過正則搜尋符合的匹配txt檔案
find . -name "*.txt"

# 使用絕對路徑不分大小寫搜尋檔案
find /home -iname file.txt
```
2. 指定檔案修改與存取時間搜尋
```shell
# 搜尋當前目錄下過去5天內檔案狀態有被存取過的檔案
find . -atime -5

# 搜尋當前目錄下過去5分鐘檔案狀態有被修改過的檔案
find . -cmin -5

# 搜尋當前目錄下過去5天檔案內容有被修改過的檔案
find . -mtime -5
``` 
> * atime（Accesstime）指的是文件最後一次被訪問的時間；
> * mtime（Modifytime）指的是文件內容被修改的時間，但不包括權限的修改，比如用vim編輯器修改內容；
> * ctime（Changetime）指的是文件的權限、擁有者、所屬組及鏈接數發上改變的時間。
3. 指定檔案類型搜尋
```shell
# 搜尋當前目錄及子目錄下，類型為文件
find . -type f

# 搜尋當前目錄及子目錄下，類型為目錄
find . -type d
```
> * b: 區塊裝置文件
> * c: 字型裝置文件
> * d: 目錄
> * p: 具名的pipe(FIFO)
> * f: 一般的檔案
> * l: 連結檔，如果與 -L 或 -follow 參數同時使用時，就只會搜尋到有問題的連結檔，如果想要與 -L 同時使用，請改用 -xtype
> * s: socket 檔案
4. 指定檔案權限搜尋
```shell
# 搜尋當前目錄下權限為777的檔案
find . -type f -perm 777

# 搜尋當前目錄下權限不是777的檔案
find . -type f ! -perm 777

# 搜尋當前目錄下權限為644而且有SGID的檔案
find . -type f -perm 2644

# 搜尋當前目錄下，user只有read的權限的檔案
find . -type f -perm /u=r
```
> * 如果不帶有任何前綴，則只有完全符合的檔案才會成功匹配
> * 如果帶有`-`，則代表同時符合，任何一類用戶（ugo）的權限中的每一位（rwx）都要同時符合mode所表示的條件，9位權限之間存在“與”關係。
> * 如果帶有`/`，則代表至少符合，任何一類用戶（ugo）的權限中的任何一位（rwx）符合mode所表示的條件即可，9位權限之間存在“或”關係。
5. 指定檔案屬性搜尋
```shell
# 搜尋當前目錄下，user為root的檔案
find . -user root

# 搜尋當前目錄下，group為root的檔案
find . -group root
```
6. 指定檔案大小搜尋
```shell
# 搜尋當前目錄下，檔案大小剛好是50MB的檔案
find . -size 50M

# 搜尋當前目錄下，檔案大小介於50MB到100MB之間的檔案
find . -size +50M -size -100M

# 搜尋當前目錄下，大於100MB的檔案並將其刪除
find . -size +100M -exec rm -rf {} \;
```

## 參考資料
* [man find](https://man7.org/linux/man-pages/man1/find.1.html)
* [SGID](http://linux.vbird.org/linux_basic/0220filemanager.php#sgid)
* [Unix/Linux 的 find 指令使用教學、技巧與範例整理](https://blog.gtwang.org/linux/unix-linux-find-command-examples/)
* [根据文件属性或权限进行find查找](https://blog.51cto.com/yttitan/1935023)

