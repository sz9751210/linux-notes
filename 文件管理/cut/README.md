# cut

- 用途：文字處理工具，可以將每一行文字的部分字元或是欄位擷取出來

## 語法

```shell
cut [OPTIONS] FILE
```

## 參數

| 參數                    | 說明                                               |
| ----------------------- | -------------------------------------------------- |
| -b, --bytes=LIST        | 擷取指定的範圍，以 bytes 作為單位                  |
| -c, --characters=LIST   | 擷取指定的範圍，以字元數量作為單位                 |
| -d, --delimiter=DELIM   | 指定分隔字元，預設是用 tab 作為分隔                |
| -f, --fields=LIST       | 輸出指定的範圍，這個是每行資料的第幾個欄位作為區分 |
| -n                      | with -b: don't split multibyte characters          |
| --complement            | 排除未擷取的欄位                                   |
| -s, --only-delimited    | 如果該行沒有分隔字元，不會顯示該行資料             |
| --output-delimiter=字串 | 改變輸出欄位的分隔字元                             |

## 基本操作
1. 擷取字元
```shell
# 擷取從第二個字元到最後
cut -c 2- file

# 擷取從開始到第二個字元
cut -c -2 file

# 擷取第2-3,5-8,10-12個字元
cut -c 2-3,5-8,10-12 file
```

2. 排除字元
```shell
# 排除2-5字元，其餘都擷取
cut -c 2-5 --complement
```

3. 擷取欄位
```shell
# 將逗號當作分隔符，擷取第二個欄位
cut -d , -f 2 file

# 將逗號當作分隔符，擷取第1-3個欄位以及第五個欄位
cut -d , -f 1-3,5 file
```

4. 排除欄位
```shell
# 排除第二個欄位，擷取剩餘的欄位
cut -d , -f 2 --complement file
```

5. 改變輸出欄位分隔字元
```shell
# 將逗號當作分隔符，擷取第1,3欄位並將分隔符從,改成:
cut -d , -f 1,3 --output-delimiter=":"
```

6. 組合技
```shell
# 找出所有python程式的PID與指令內容
ps aux | grep python | sed 's/\s\+/ /g' | cut -d ' ' -f 2,11-
```

## 參考資料
* [Linux 的 cut 擷取部份字元、欄位指令教學與常用範例整理 - G. T. Wang (gtwang.org)](https://blog.gtwang.org/linux/linux-cut-command-tutorial-and-examples/)
* [cut 指令: 擷取檔案每行指定範圍資料 (ltsplus.com)](https://www.ltsplus.com/linux/cut-command)
* [Bash Cut Command with Examples (linuxhint.com)](https://linuxhint.com/bash-cut-command-examples/)
## 相關指令(可選)
* sed
* awk