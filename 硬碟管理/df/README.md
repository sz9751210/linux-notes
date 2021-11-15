# df(disk free)

- 用途：顯示當前系統上的硬碟使用狀況

## 語法

```shell
df [OPTIONS] [path or file]
```

## 參數

| 參數                         | 說明                                                                                      |
| ---------------------------- | ----------------------------------------------------------------------------------------- |
| -a, --all                    | 顯示所有檔案系統的使用狀況，包活/proc等特殊檔案系統                                       |
| -B, --block-size=SIZE        | 使用{SIZE}大小的Blocks檔案                                                                |
| --direct                     | show statistics for a file instead of mount point                                         |
| --total                      | 顯示大小的總計                                                                            |
| -h, --human-readable         | 以適合人閱讀的格式顯示                                                                    |
| -H, --si                     | 與`-h`一樣，但會用1MB = 1000KB計算，而不使用1MB = 1024KB                                  |
| -i, --inodes                 | 顯示inode資訊，不列出已使用block                                                          |
| -k                           | 以KB為單位顯示                                                                            |
| -m                           | 以MB為單位顯示                                                                            |
| -l, --local                  | 只顯示本機硬碟                                                                            |
| --no-sync                    | 在取得資料前不sync(default)                                                               |
| --output[=FIELD_LIST]        | use the output format defined by FIELD_LIST, or print all fields if FIELD_LIST is omitted |
| -P, --portability            | 使用POSIX格式輸出                                                                         |
| --sync                       | 在取得資料前sync                                                                          |
| -t TYPE, --type=TYPE         | 指定要顯示的類型                                                                          |
| -T TYPE, --print-type        | 顯示檔案系統類型                                                                          |
| -x TYPE, --exclude-type=TYPE | 指定要排除的類型                                                                          |
| -v                           | Ignored, included for compatibility reasons                                               |

## 基本操作
1. 顯示當前硬碟用量
```shell
df
```

2. 指定掛載點
```shell
df /
```

3. 顯示所有檔案系統硬碟用量
```shell
df -a
```

4. 以較容易閱讀的格式顯示
```shell
df -h
```

5. 以KB為單位顯示
```shell
df -k
```

6. 顯示總計大小
```shell
df --total
```

7. 顯示檔案系統
```shell
df -T
```

8. 指定要顯示的檔案系統
```shell
df -t tmpfs
```

9. 指定要排除的檔案系統
```shell
df -x
```

10. 顯示inode訊息而不是block訊息
```shell
df -i
```

11. 在取得硬碟資料前sync
```shell
df --sync
```

12. 只顯示本機硬碟
```shell
df -l
```
## 參考資料
* https://www.geeksforgeeks.org/df-command-in-linux-with-examples/
* https://blog.gtwang.org/linux/linux-df-command-check-disk-space-usage-tutorial-script-example/
## 相關指令(可選)
* du