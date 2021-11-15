# free

- 用途：檢查系統內實體記憶體及 Swap 的使用情況

## 語法

```shell
free [OPTIONS]
```

## 參數

| 參數              | 說明                                 |
| ----------------- | ------------------------------------ |
| -b, --bytes       | 單位以 Bytes 顯示                    |
| -k, --kilo        | 單位以 KB 顯示                       |
| -m, --mega        | 單位以 MB 顯示                       |
| -g, --giga        | 單位以 GB 顯示                       |
| --tera            | 單位以 TB 顯示                       |
| --peta            | 單位以 PB 顯示                       |
| -h, --human       | 以人類可讀格式顯示記憶體使用情況     |
| --si              | 使用1000進位而不是1024               |
| -l, --lohi        | 顯示詳細的低內存和高內存統計信息     |
| -t, --total       | 顯示實體記憶體加上 Swap 的合共記憶體 |
| -s N, --seconds N | 指定更新頻率                         |
| -c N, --count N   | 指定更新次數                         |
| -w, --wide        | wide output                          |

## 欄位說明

```shell
              total        used        free      shared  buff/cache   available
Mem:           1.8G        685M        485M        8.7M        666M        995M
Swap:          2.0G          0B        2.0G
```

| 參數       | 說明                                                                                                         |
| ---------- | ------------------------------------------------------------------------------------------------------------ |
| total      | 物理記憶體大小，就是機器實際的記憶體                                                                         |
| used       | 已使用的記憶體大小，這個值包括了 cached 和 應用程序實際使用的記憶體，`used = total - free - buffers - cache` |
| free       | 未被使用的記憶體大小                                                                                         |
| shared     | 共享記憶體大小，是進程間通信的一種方式，可忽略                                                               |
| buff/cache | 被緩衝區佔用的記憶體大小，如果希望緩衝區和緩存顯示在兩個單獨的列中，請使用`-w`選項                           |
| available  | 可用於啟動新應用程序的內存量的估計，無需交換。                                                               |

## 基本操作
1. 以人類可讀格式顯示記憶體使用狀況
```shell
free -h
```

2. 以KB格式顯示
```shell
free -k
```

3. 每五秒更新一次，更新10次
```shell
free -s 5 -c 10
```

4. 以人類可讀格式顯示total並把buff/cache單獨出來
```shell
free -htw
```

## 參考資料
* https://linuxize.com/post/free-command-in-linux/
* https://blog.gtwang.org/linux/linux-cache-memory-linux/
* https://xyz.cinc.biz/2016/06/linux-memory-used-free.html
* https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/free.html
## 相關指令
* df
* top