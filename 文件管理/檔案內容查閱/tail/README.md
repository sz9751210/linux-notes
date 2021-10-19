# tail

- 用途：印出結尾，與 head 相法的功用

## 語法

```shell
tail [option] [fileName]
```

## 參數

| 參數        | 說明                                                             |
| ----------- | ---------------------------------------------------------------- |
| -n <行數>   | 顯示尾部 N 行的訊息 (N 為數字)                                   |
| -c <字節數> | 顯示尾部倒數 N bytes 的字元 (N 為數字)                           |
| -q          | 隱藏文件名                                                       |
| -v          | 顯示文件名                                                       |
| -f          | 循環讀取，持續監看最新追加的內容，常用於查閱正在改變的日誌文件。 |

## 基本操作

假設有一個檔案 tail_test 長這樣

```text
test1
test2
test3
```

1. 查看後 2 行

```shell
tail -n 2 head_test

# output
test2
test3
```

2. 查看後兩個字

```shell
head -c 2 tail_test

# output
t3%
```

3. 顯示文件名

```shell
tail -v tail_test

# output
==> tail_test <==
test1
test2
test3
```



## 相關指令(可選)
* grep
* sort
