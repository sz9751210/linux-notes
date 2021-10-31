# service

- 用途：管理系統中的服務

## 語法

```shell
systemctl [OPTIONS] command or name
```

## 參數

| 參數 | 說明 |
| ---- | ---- |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |

##　指令
| 參數 | 說明 |
| ---- | ---- |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |

## service檔說明

[Unit]
Description:描述
After：在network.target,auditd.service啟動後才啟動
ConditionPathExists: 執行條件

[Service]
EnvironmentFile:變量所在的文件
ExecStart: 執行啟動腳本
Restart: fail時重啟

[Install]
Alias:服務別名
WangtedBy: 多用戶模式下需要的


## 基本操作

## 參考資料
* https://blog.csdn.net/skh2015java/article/details/94012643

* https://blog.gtwang.org/linux/linux-basic-systemctl-systemd-service-unit-tutorial-examples/

* https://www.tokfun.net/os/linux/linux-service-systemctl/

* https://chenhh.gitbooks.io/ubuntu-linux/content/service.html
## 相關指令(可選)
