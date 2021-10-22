# pwd(print work directory)

- 用途：顯示目前工作目錄的絕對路徑名稱

## 語法

```shell
pwd [OPTIONS]
```

## 參數

| 參數 | 說明 |
| ---- | ---- |
|  -P    |   輸出物理路徑   |
|  -L    |   目錄連接鏈接時，輸出連接路徑   |
## 基本操作
1. 顯示當前路徑
```shell
pwd
```

2. 顯示軟連結所指向的路徑
假設連結symlink指向test1/test2
```shell
pwd -P 

# output
test1/test2

```

3. 顯示軟連結的連接路徑
假設連結symlink指向test1/test2
```shell
pwd -L

# output
symlink

```
4. 刪掉路徑會顯示當前路徑
```shell
cd aaa/bbb
rm -rf aaa/bbb
pwd

# output
aaa/bbb
```
