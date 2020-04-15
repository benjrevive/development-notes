# linux-notes
linux-related notes

## Table of Contents <!-- omit in toc -->
- [bash 相關](#bash-相關)
  - [啟用終端機顯示顏色](#啟用終端機顯示顏色)
  - [清空畫面](#清空畫面)
  - [清空輸入區](#清空輸入區)
  - [清除輸入區最後一個單詞](#清除輸入區最後一個單詞)
  - [將輸入區內容註解](#將輸入區內容註解)
  - [再次執行先前指令](#再次執行先前指令)
  - [查看最近1000筆以前的指令記錄](#查看最近1000筆以前的指令記錄)
  - [使history指令的輸出結果包含時間戳](#使history指令的輸出結果包含時間戳)
- [套件相關](#套件相關)
  - [列出所有已安裝套件](#列出所有已安裝套件)
- [系統資訊](#系統資訊)
  - [顯示作業系統版本](#顯示作業系統版本)
  - [設定主機名稱](#設定主機名稱)
- [網路相關](#網路相關)
  - [列出所有網卡硬體資訊](#列出所有網卡硬體資訊)
  - [列出所有網卡名稱](#列出所有網卡名稱)
  - [顯示所有網卡流量](#顯示所有網卡流量)
  - [在 Ubuntu 中停用 IPv6 功能](#在-ubuntu-中停用-ipv6-功能)
- [畫面相關](#畫面相關)
  - [新增 Ubuntu 螢幕解析度設定中未出現的項目](#新增-ubuntu-螢幕解析度設定中未出現的項目)
- [在 Ubuntu 中 VMware 共用資料夾掛載路徑](#在-ubuntu-中-vmware-共用資料夾掛載路徑)
- [新增使用者帳戶:](#新增使用者帳戶)
- [將帳戶加入至 sudo 群組:](#將帳戶加入至-sudo-群組)
- [顯示所有使用者帳戶資料:](#顯示所有使用者帳戶資料)
- [顯示所有使用者帳號:](#顯示所有使用者帳號)
- [顯示所有群組:](#顯示所有群組)
- [顯示使用者群組:](#顯示使用者群組)
- [刪除使用者帳戶:](#刪除使用者帳戶)
- [以名稱搜尋資料夾:](#以名稱搜尋資料夾)
- [以名稱搜尋資料夾(不分大小寫):](#以名稱搜尋資料夾不分大小寫)
- [顯示壓縮檔內容:](#顯示壓縮檔內容)
- [壓縮:](#壓縮)
- [解壓縮:](#解壓縮)
- [顯示已安裝套件:](#顯示已安裝套件)
- [在背景執行指令(使用者中斷連線後仍繼續執行):](#在背景執行指令使用者中斷連線後仍繼續執行)
- [Vim 唯讀模式](#vim-唯讀模式)
- [diff unified format](#diff-unified-format)
- [show all sudoers](#show-all-sudoers)
- [resize LVM](#resize-lvm)
- [快速安裝 L2TP/IPSec VPN](#快速安裝-l2tpipsec-vpn)
- [shell script 參數與判斷式](#shell-script-參數與判斷式)
- [apt/apt-get autoremove 的危險性](#aptapt-get-autoremove-的危險性)

## bash 相關

### 啟用終端機顯示顏色

#### Ubuntu
將 `~/.bashrc` 檔案中 `#force_color_prompt=yes` 註解符號 `#` 刪除，執行 `source ~/.bashrc` 或重新登入終端機

#### CentOS
在 `~/.bashrc` 檔案尾端加入：
```bash
PS1='\[\e[01;36m\]\u\[\e[01;37m\]@\[\e[01;33m\]\H\[\e[01;37m\]:\[\e[01;32m\]\w\[\e[01;37m\]\$\[\033[0;37m\] '
```
執行 `source ~/.bashrc` 或重新登入終端機

##### 顯示 Git 狀態的版本
從 Git 官方專案取得 `contrib/completion/git-prompt.sh` 置於家目錄，並在 `~/.bashrc` 檔案尾端加入以下片段後執行 `source ~/.bashrc` 或重新登入終端機：
```bash
. ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
PS1='\[\e[01;36m\]\u\[\e[01;37m\]@\[\e[01;33m\]\H\[\e[01;37m\]:\[\e[01;32m\]\w\[\e[01;37m\]\[\e[35m\]$(__git_ps1 " (%s)")\[\e[m\]\$\[\033[0;37m\] '
```

### 清空畫面
執行指令 `clear` 或 <kbd>Ctrl</kbd>+<kbd>L</kbd>

### 清空輸入區
<kbd>Ctrl</kbd>+<kbd>U</kbd> (復原: <kbd>Ctrl</kbd>+<kbd>Y</kbd>)

### 清除輸入區最後一個單詞
<kbd>Ctrl</kbd>+<kbd>W</kbd> (復原: <kbd>Ctrl</kbd>+<kbd>Y</kbd>)

### 將輸入區內容註解
<kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>#</kbd>

### 再次執行先前指令
執行 `history` 查看指令記錄與其編號，執行 `!<number>` 以再次執行該指令。  
範例：
```
$ ls
a.txt  b.txt

$ cat a.txt
hello world

$ history
...
  103  ls
  104  cat a.txt
  105  history

$ !103
a.txt  b.txt
```

### 查看最近1000筆以前的指令記錄
使用 `less`、`view` 之類指令查看 `~/.bash_history`

### 使history指令的輸出結果包含時間戳

於 `~/.bashrc` 內容末端新增以下片段後執行 `source ~/.bashrc` 或重新登入終端機：
```bash
HISTTIMEFORMAT='%F %T '
```
※若僅需作用於該次連線階段，則執行指令 `export HISTTIMEFORMAT='%F %T '` 即可

## 套件相關

### 列出所有已安裝套件

執行 `dnf list installed`

## 系統資訊

### 顯示作業系統版本

#### Ubuntu

```
lsb_release -a
```

#### CentOS 8

```
cat /etc/system-release
```

#### General
```
cat /etc/os-release
```

### 設定主機名稱

#### CentOS 8
```
# hostnamectl set-hostname <hostname>
```

## 網路相關

### 列出所有網卡硬體資訊  
```bash
lspci | grep -i eth  
```

### 列出所有網卡名稱
```bash
ip link
```  

### 顯示所有網卡流量
```bash
ifconfig -s -a
```

### 在 Ubuntu 中停用 IPv6 功能
編輯 `/etc/sysctl.conf`，在檔案最後加上以下內容後，
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
執行：
```bash
sudo sysctl -p
```

## 畫面相關

### 新增 Ubuntu 螢幕解析度設定中未出現的項目
```bash
cvt 1920 1080 60
```
output:  
```bash
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```
依照顯示的參數執行以下兩行指令後，螢幕解析度設定中應會出現所設的項目  
(第二行的 Virtual1 適用於虛擬機，實體機換成 VGA-0)
```bash
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode Virtual1 1920x1080_60.00
```
使用指令設定螢幕解析度  
(參數 Virtual1 適用於虛擬機，實體機換成 VGA-0)
```bash
xrandr --output Virtual1 --mode "1920x1080_60.00"
```
新增 ~/.xprofile 並將上述指令如下填入，往後每次開機後就不用重新再設定一次
```bash
#!/bin/sh
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode Virtual1 1920x1080_60.00
```

*How to set a custom resolution? https://askubuntu.com/questions/377937*

## 在 Ubuntu 中 VMware 共用資料夾掛載路徑
```
/mnt/hgfs/
```

## 新增使用者帳戶:
```bash
sudo adduser <username>
```

## 將帳戶加入至 sudo 群組: 
```bash
sudo usermod -aG sudo <username>
```

## 顯示所有使用者帳戶資料: 
```bash
cat /etc/passwd
```

## 顯示所有使用者帳號: 
```bash
awk -F':' '{ print $1}' /etc/passwd
```

## 顯示所有群組: 
```bash
cat /etc/group
```

## 顯示使用者群組: 
```bash
groups [username]
```

## 刪除使用者帳戶: 
```bash
sudo deluser <username> --remove-home --backup
```

## 以名稱搜尋資料夾: 
```bash
find <path> -name <dirname> -type d
```

## 以名稱搜尋資料夾(不分大小寫): 
```bash
find <path> -iname <dirname> -type d
```

## 顯示壓縮檔內容: 
```bash
tar -tvf <file>
```

## 壓縮: 
```bash
tar -zcvpf <output-filename> <source>
```

## 解壓縮: 
```bash
tar [-C <output-path>] -zxvf <file>
```

## 顯示已安裝套件: 
```bash
apt list [<packagename>] --installed
```

## 在背景執行指令(使用者中斷連線後仍繼續執行): 
```bash
nohup <command> &
```

## Vim 唯讀模式
```bash
vim -R <file>
```
或
```bash
view <file>
```

## diff unified format
## show all sudoers
## resize LVM
https://www.linuxidc.com/Linux/2017-05/143724.htm
https://sc8log.blogspot.com/2017/03/linux-lvm-lvm.html
https://blog.moa.tw/2018/12/ubuntu-1804-root-lvm-volume.html

## 快速安裝 L2TP/IPSec VPN
*L2TP/IPSec一键安装脚本 | 秋水逸冰 https://teddysun.com/448.html*

## shell script 參數與判斷式
```bash
echo "\$# = " $#
if [ $# -gt 0 ]; then
    if [ $1 = "1GB" -o $1 = "10GB" ]; then
        echo "GB"
        touch test_$1.txt
    elif [ $1 = "100GB" ]; then
        echo "100GB"
    else
        echo "\$1 = " $1
    fi
else
    echo "no args"
fi
```

## apt/apt-get autoremove 的危險性