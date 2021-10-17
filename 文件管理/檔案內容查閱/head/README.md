# head

- 用途：用來顯示開頭的文字區塊，看開頭檔案用的

## 語法
```shell
head [option] [fileName]  
```

## 參數

|參數   |說明   |
|---|---|
| -n <行數>  | 顯示前幾行  |
| -c <字節數>  | 顯示前幾個字節數  |
| -q  | 隱藏文件名  |
|  -v | 顯示文件名  |

## 基本操作
假設有一個檔案head_test長這樣
```text
test1
test2
test3
```
1. 查看前2行
```shell
head -n 2 head_test

# output 
test1
test2
```
2. 查看前兩個字
```shell
head -c 2 head_test

# output
te%
```
3. 顯示文件名
```shell
head -v head_test

# output
==> head_test <==
test1
test2
test3
```