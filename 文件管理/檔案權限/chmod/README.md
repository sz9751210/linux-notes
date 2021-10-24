# chmod(change mode)

- 用途：控制用戶對文件的權限，linux 的文件權限分為三種身分，owner/group/others，而權限也分為三種，read/write/execute，權重如下表格

| 權限 | 權重 |
| ---- | ---- |
| r    | 4    |
| w    | 2    |
| x    | 1    |

## 語法

```shell
chmod [OPTIONS] [mode] [檔案或目錄]
```

## 參數

| 參數                  | 說明                                                       |
| --------------------- | ---------------------------------------------------------- |
| -c, --changes         | 效果類似"-v"參數，但僅回報更改的部分。                     |
| -f, --silent, --quiet | 不顯示錯誤資訊。                                           |
| -v, --verbose         | 顯示指令執行過程。                                         |
| --no-preserve-root    | 取消對 root 文件系統的保護                                 |
| --preserve-root       | 保留對 root 文件系統的保護                                 |
| --reference=RFILE     | 把指定文件或目錄的權限全部設成和參考文件或目錄的權限相同。 |
| -R, --recursive       | 遞迴處理，將指定目錄下的所有檔及子目錄一併處理。           |

## 基本操作

1. 將檔案變成user可執行
假設原本檔案權限為`-rw-rw-r--`

| 指令  | mode |
| ----- | ---- |
| chmod | u+x  |
| chmod | u=rwx  |
| chmod | 764     |

## 相關指令(可選)
