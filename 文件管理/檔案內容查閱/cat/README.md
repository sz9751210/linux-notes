# cat

- 用途：查看文件，把檔案串連接後傳到基本輸出

## 使用權限

所有使用者

## 語法

```shell
cat [-AbeEnstTuv] [--help] [--version] fileName
```

## 參數

| 參數                   | 說明                                               |
| ---------------------- | -------------------------------------------------- |
| -A, --show-all         | 等價於-vET                                         |
| -b, --number-nonblank  | 和 -n 相似，只不過對於空白行不編號                 |
| -e                     | 等價於-vE                                          |
| -E, --show-ends        | 在每一行末端加入$                                  |
| -n, --number           | 由 1 開始對所有輸出的行數編號                      |
| -s, --squeeze-blank    | 當遇到有連續兩行以上的空白行，就代換為一行的空白行 |
| -t                     | 等價於-vT                                          |
| -T, --show-tabs        | 以^I 取代 TAB                                      |
| -u                     | 輸出時不必經過緩衝區。（原來是預設為使用緩衝區）。 |
| -v, --show-nonprinting | 除了 LFD 及 TAB 之外，使用^及 M-表示法顯示字元     |
| --help                 | 列出幫助資訊                                       |
| --version              | 列出版本資訊                                       |

## 基本操作
1. 查看檔案
```shell
cat test1
```
2. 查看檔案並顯示行號

假設有個檔案test2長這樣
```
test1


test2
```

```shell
cat -n test2

# ountput
    1 test1
    2
    3 
    4 test2
```
如果要對空白行取消編號的話可改用-b選項
```shell
cat -b test2

# ountput
    1 test1


    2 test2
```
如果要把一行以上的空白行合併為一行可使用-s選項
```shell
cat -s test2

# output
aaa

bbb
```