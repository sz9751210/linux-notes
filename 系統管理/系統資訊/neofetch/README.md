# neofetch

- 用途：顯示正在使用的操作系統或 Linux 發行版，包括主題、圖標、硬體配置等訊息。

## 安裝教學
### 環境
* CentOS 7
### 步驟
1. 安裝epel-release
```shell
sudo yum install epel-release
```
2. 添加第三方軟件源
```shell
sudo curl -o /etc/yum.repos.d/konimex-neofetch-epel-7.repo https://copr.fedorainfracloud.org/coprs/konimex/neofetch/repo/epel-7/konimex-neofetch-epel-7.repo
```

3. 使用yum套件管理器安裝
```shell
sudo yum install neofetch
```

## 語法

```shell
neofetch [OPTIONS]
```

## 配置文件路徑
~/.config/neofetch/config.conf
可透過修改printinfo()函數來調整你想顯示在終端的系統訊息

## 基本操作
```
neofetch

# output
                 ..                    alan@localhost.localdomain
               .PLTJ.                  --------------------------
              <><><><>                 OS(作業系統): CentOS Linux 7 (Core) x86_64
     KKSSV' 4KKK LJ KKKL.'VSSKK        Host(物理幾名稱): VirtualBox 1.2
     KKV' 4KKKKK LJ KKKKAL 'VKK        Kernel(內核版本): 3.10.0-1160.42.2.el7.x86_64
     V' ' 'VKKKK LJ KKKKV' ' 'V        Uptime(系統運作時間): 6 hours, 50 mins
     .4MA.' 'VKK LJ KKV' '.4Mb.        Packages(軟件包總數（默認安裝和其他）): 606 (rpm)
   . KKKKKA.' 'V LJ V' '.4KKKKK .      Shell(Shell及其版本): zsh 5.8
 .4D KKKKKKKA.'' LJ ''.4KKKKKKK FA.    Terminal(終端機): /dev/pts/0
<QDD ++++++++++++  ++++++++++++ GFD>   CPU: Intel i7-9750H (1) @ 2.592GHz
 'VD KKKKKKKK'.. LJ ..'KKKKKKKK FV     GPU: 00:02.0 VMware SVGA II Adapter
   ' VKKKKK'. .4 LJ K. .'KKKKKV '      Memory: 740MiB / 1837MiB
      'VK'. .4KK LJ KKA. .'KV'
     A. . .4KKKK LJ KKKKA. . .4
     KKA. 'KKKKK LJ KKKKK' .4KK
     KKSSA. VKKK LJ KKKV .4SSKK
              <><><><>
               'MKKM'
                 ''

```



## 參考資料
https://github.com/dylanaraps/neofetch
