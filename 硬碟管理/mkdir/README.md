# mkdir
* 用途：建立目錄

## 語法
```shell
mkdir [option] dirName
```
## 參數
| 參數  |說明   |
|---|---|
|-m, --mode=MODE   | 	設定文件模式（file mode），就像是 `chmod` 一樣  |
| -p, --parents  | 可以建立多層資料夾目錄（會自動建立尚不存在的父目錄）  |
| -v, --verbose  |顯示建立訊息   |
|--help   |顯示幫助說明   |
| --version  | 顯示版本資訊並離開  |
| -Z, --context[=CTX]  | 對新建目錄進行 SELinux 安全設定。  |

## 基本操作
1. 新建一個空目錄
```shell
mkdir test1
```
2. 遞歸建立多個目錄
```shell
mkdir -p test1/test2
```
3. 建立權限為777的目錄
```shell
mkdir -m 777 test3
```
4. 建立目錄並顯示資訊
```shell
mkdir -v test4

# output
mkdir: created directory ‘test4’
```

## 相關指令
* chmod
* chown
* umask
* 檔案與目錄存取權限