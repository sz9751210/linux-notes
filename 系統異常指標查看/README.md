# 系統異常指標查看

## CPU

1. top
```shell
top
P
b
x
y
```

```shell
top -o %MEM
```

2. ps
```shell
ps aux --sort -pcpu
```


## MEM

1. top
```shell
top
M
b
x
y
```

```shell
top -o %CPU
```

2. ps
```shell
ps aux --sort -pmem
```



## swap

1. free
```shell
free -h
```

2. vmstat
```shell
vmstat
```

3. swapon
```shell
swapon -s
```

4. proc_file
```shell
cat /proc/swaps
```


5. shell
```shell
for file in /proc/*/status ; do awk '/VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | sort -k 2 -n -r | less
```

### 參考資料
* https://www.tecmint.com/commands-to-monitor-swap-space-usage-in-linux/
* https://www.cyberciti.biz/faq/linux-which-process-is-using-swap/
* https://mini.nidbox.com/diary/read/9920500
* https://blog.longwin.com.tw/2017/02/linux-find-use-swap-process-2017/


## disk

1. df
```shell
df -h
```

## conn

1. netstat
```shell
# 查看80 port的總連線數
netstat -na | grep 80 | wc -l

# 統計連線的ip
netstat -ntu | grep ESTAB | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -nr
```




