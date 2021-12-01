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
* [8 Useful Commands to Monitor Swap Space Usage in Linux (tecmint.com)](https://www.tecmint.com/commands-to-monitor-swap-space-usage-in-linux/)
* [Linux Find Out What Process Are Using Swap Space - nixCraft (cyberciti.biz)](https://www.cyberciti.biz/faq/linux-which-process-is-using-swap/)
* [筆記: Linux 建立 Swap, 以及 Swap 使用狀況監控, OOM @mini box 迷你盒子 - nidBox親子盒子](https://mini.nidbox.com/diary/read/9920500)
* [Linux 查看正在吃 swap 的程式 – Tsung's Blog (longwin.com.tw)](https://blog.longwin.com.tw/2017/02/linux-find-use-swap-process-2017/)


## disk

1. df
```shell
df -h
```

2. du
```shell
du -shc /path/*

du -h -x --max-depth=1
```


## conn

1. netstat
```shell
# 查看80 port的總連線數
netstat -na | grep 80 | wc -l

# 統計連線的ip
netstat -ntu | grep ESTAB | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -nr
```




