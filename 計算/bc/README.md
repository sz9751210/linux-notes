# bc

- 用途：計算機，可作基本的數學運算，支援任意精度的交互執行計算機語言

## 語法

```shell
bc [OPTIONS]] [file ...]
```

## 參數

| 參數              | 說明                             |
| ----------------- | -------------------------------- |
| -i  --interactive | 強制進入交互模式                 |
| -l  --mathlib     | 定義使用的標準數學庫，自訂小數點 |
| -q  --quiet       | 不顯示正常的GNU bc環境信息       |
| -s  --standard    | 啟動POSIX模式下的bc程序          |
| -w  --warn        | 對POSIX bc的擴展給出警告信息     |

## 基本操作
1. 進入交互模式
```shell
bc or bc -i
```

2. 精確模式
```shell
bc -l
```

3. 進入交互模式後自訂小數點後輸出位數
```shell
bc

scale=5
100/7
```

4. 透過pipe將運算式給bc計算
```shell
echo 'scale=5; 100/7' | bc
```

5. 將計算結果放入變數儲存起來
```shell
ans=$(echo 'scale=5; 100/7' | bc)
echo $ans
```

## 參考資料
* [bc命令_Linux bc 命令用法详解：算术操作精密运算工具 (linuxde.net)](https://man.linuxde.net/bc)
* [Linux 計算機 bc 指令用法教學與範例 - G. T. Wang (gtwang.org)](https://blog.gtwang.org/linux/linux-bc-command-tutorial-examples/)
* [Linux bc 命令 | 菜鸟教程 (runoob.com)](https://www.runoob.com/linux/linux-comm-bc.html)
* [bc命令详解 - 马昌伟 - 博客园 (cnblogs.com)](https://www.cnblogs.com/machangwei-8/p/10388510.html)
## 相關指令
* calc
* gcalccmd
* qalc
* expr & echo