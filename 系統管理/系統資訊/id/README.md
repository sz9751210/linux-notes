# id

- 用途：顯示用戶的ID，以及所屬群組的ID。

## 語法

```shell
id [OPTIONS] userName
```

## 參數
| 參數          | 說明                     |
| ------------- | ------------------------ |
| -Z, --context | 顯示當前用戶的安全上下文 |
| -g, --group   | 顯示所屬群組ID           |
| -G, --groups  | 顯示所有群組ID           |
| -n, --name    | 顯示用戶                 |
| -r, --real    | 顯示實際ID               |
| -u, --user    | 顯示用戶ID               |

## 基本操作
1. 顯示當前用戶訊息
```shell
id

# output
uid=1000(alan) gid=1000(alan) groups=1000(alan),996(vboxsf) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```
2. 顯示用戶群組id
```shell
id -g

# output
1000
```
3. 顯示指定用戶訊息
```shell
id root
```