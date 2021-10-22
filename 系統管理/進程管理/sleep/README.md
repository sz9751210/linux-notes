# sleep

- 用途：用來將當前動作延遲一段時間

## 語法

```shell
sleep number[smhd]
```

## 參數

| 參數 | 說明 |
| ---- | ---- |
|  number    | 時間長度，後面可接s、m、h、d。s為秒，m為分鐘，h為小時，d為天數    |

## 基本操作
顯示目前時間後延遲一分鐘再顯示一次時間
```shell
date;sleep 1m;date
```

