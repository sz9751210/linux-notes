# chown

- 用途：變更文件或目錄的權限

## 語法

```shell
chmod [OPTIONS] [user:group] file or dir
```

## 參數

| 參數                               | 說明                                                                      |
| ---------------------------------- | ------------------------------------------------------------------------- |
| -c, --changes                      | 效果類似`-v`，但僅回傳更改的部分                                          |
| -f, --silent, --quiet              | 不顯示錯誤訊息                                                            |
| -v, --verbose                      | 顯示指令執行過程                                                          |
| --dereference                      | 效果和`-h`參數相同                                                        |
| -h, --no-dereference               | 只對軟連結的文件做修改，而不更動其它任何相關文件                          |
| --from=CURRENT_OWNER:CURRENT_GROUP | 確認修改前的擁有者及所屬群組正確才進行修改                                |
| --no-preserve-root                 | do not treat '/' specially (the default)                                  |
| --preserve-root                    | fail to operate recursively on '/'                                        |
| --reference=RFILE                  | 把指定文件或目錄的擁有者與所屬群組全都改成和參考文件或目錄一樣            |
| -R, --recursive                    | 遞歸處理，將指定目錄下的所有文件以及子目錄一併處理                        |
| -H                                 | if a command line argument is a symbolic link to a directory, traverse it |
| -L                                 | traverse every symbolic link to a directory encountered                   |
| -P                                 | do not traverse any symbolic links (default)                              |
## 基本操作
1. 將檔案或目錄修改擁有者
```shell
chown alan file1
```
2. 將檔案或目錄修改所屬群組
```shell
chown :alangroup file1
```
3. 同時修改擁有者及所屬組
```shell
chown alan:alangroup file1
```
4. 遞歸修改整個資料夾裡的所有檔案
```shell
chown -R alan:alangroup dir
```
5. 顯示執行結果
```shell
chown -v alan:alangroup file1
```
6. 不顯示錯誤訊息
```shell
chown -f alan:alangroup file1
```
7. 參考文件屬性進行修改
```shell
chown --reference=reffile file1
```
8. 事先確認擁有者與群組在進行修改
```shell
chown --from=root:root alan:alangroup file1
```
9. 只確認擁有者或是群組
```shell
# 只確認擁有者
chown --from=root alan:alangroup file1

# 只確認所屬組
chown --from=:root alan:alangroup file1
```


## 參考資料
* https://blog.gtwang.org/linux/linux-chown-command-tutorial/

