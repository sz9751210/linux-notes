# passwd

- 用途：修改使用者密碼

## 語法

```shell
passwd [OPTIONS] username
```

## 參數

| 參數                | 說明                                                |
| ------------------- | --------------------------------------------------- |
| -k, --keep-tokens   | 保留未過期的驗證 token                              |
| -d, --delete        | 刪除 named 帳號的密碼 (只有 root 可執行)            |
| -l, --lock          | 鎖住 named 帳號的密碼 (只有 root 可執行)            |
| -u, --unlock        | 解開 named 帳號的密碼鎖定 (只有 root 可執行)        |
| -e, --expire        | 讓 named 帳號的密碼過期 (只有 root 可執行)          |
| -f, --force         | 強制作業                                            |
| -x, --maximum=DAYS  | 最大密碼有效期限 (只有 root 可執行)                 |
| -n, --minimum=DAYS  | 最小密碼有效期限 (只有 root 可執行)                 |
| -w, --warning=DAYS  | 用戶在密碼過期前收到警告的天數 (只有root可執行)     |
| -i, --inactive=DAYS | 帳號在密碼過期後即將被停用前的天數 (只有root可執行) |
| -S, --status        | 回報 named 帳號上的密碼狀態 (只有 root 可執行)      |
| --stdin             | 由 stdin 讀取新的 token (只有 root 可執行)          |

## 基本操作
1. 修改使用者密碼
```shell
passwd myuser
```

2. 顯示使用者密碼狀態
```shell
passwd -S myuser

# output
myuser PS 2021-11-26 0 99999 7 -1
```

| 欄位                                                     | 範例       |
| -------------------------------------------------------- | ---------- |
| 帳號名稱                                                 | myuser     |
| 密碼狀態，狀態包含鎖定密碼(LK)、無密碼(NP)與可用密碼(PS) | PS         |
| 上次修改密碼時間                                         | 2021-11-26 |
| 密碼最短使用期限，單位為天                               | 0          |
| 密碼最長使用期限，單位為天                               | 99999      |
| 密碼過期前警告期間，單位為天                             | 7          |
| 密碼過期後可使用的期間，單位為天                         | -1         |

3. 刪除使用者密碼
```shell
passwd -d myuser
```

4. 讓密碼過期，強制使用者更新密碼
```shell
passwd -e myuser

# 下次登入時，就會跳出通知說要更改密碼
You are required to change your password immediately (root enforced)
WARNING: Your password has expired.
You must change your password now and login again!
Changing password for user myuser.
Changing password for myuser.
(current) UNIX password:
```

5. 鎖定與解鎖使用者密碼
```shell
passwd -l myuser
```
> 此指令會使/etc/shadow的使用者密碼欄位前面多了`!!`
> 
> 該狀態下使用者無法變更帳號密碼
> 
> 要解除鎖定可用`-u`

```shell
passwd -u myuser
```

6. 設定密碼期限
```shell
# 至少五天才能改一次密碼
passwd -n 5 myuser

# 密碼最多只能用30天
passwd -x 30 myuser

# 快過期前7天送警告
passwd -w 7 myuser

# 寬限期設定，超過5天將無法再登入
passwd -i 5 myuser
```

## 參考資料
* [Linux passwd命令 | 菜鸟教程 (runoob.com)](https://www.runoob.com/linux/linux-comm-passwd.html)
* [Linux 的 passwd 指令範例教學 - G. T. Wang (gtwang.org)](https://blog.gtwang.org/linux/linux-passwd-command-examples/)