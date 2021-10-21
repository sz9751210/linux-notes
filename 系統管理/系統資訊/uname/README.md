# uname

- 用途：顯示系統訊息(unix name)

## 語法

```shell
uname [OPTIONS]
```

## 參數

| 參數                    | 說明                                                                  |
| ----------------------- | --------------------------------------------------------------------- |
| -a, --all               | 顯示全部訊息                                                          |
| -s, --kernel-name       | 顯示系統內核名稱(預設)                                                |
| -n, --nodename          | 顯示網路主機名稱                                                      |
| -r, --kernel-release    | 顯示內核版本                                                          |
| -v, --kernel-version    | 顯示內核運行於哪個linux上，和實際發行的日期                           |
| -m, --machine           | 顯示電腦類型：x86_64(為64位元架構，如為32位元會如：x86_32)            |
| -p, --processor         | 顯示處理器類型：x86_64(為64位元架構，如為32位元會如：x86_32)          |
| -i, --hardware-platform | 顯示硬體平台類型：x86_64(硬件平台包括如CPU、儲存裝置、主機板等等硬體) |
| -o, --operating-system  | 顯示操作系統名稱：GNU/Linux(作業系統，如windows)                      |
## 基本操作
1. 顯示系統訊息
```shell
uname -a

# output
Linux localhost.localdomain 3.10.0-1160.42.2.el7.x86_64 #1 SMP Tue Sep 7 14:49:57 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
2. 顯示操作系統名稱
```shell
uname or uname -s

# output
Linux
```
也可使用 `cat /etc/os-release`來查看系統訊息
