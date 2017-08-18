# linux
linux-related notes

## 列出所有網卡硬體資訊  
```bash
lspci | grep -i eth  
```
## 列出所有網卡名稱
```bash
ip link
```  
## 顯示所有網卡流量
```bash
ifconfig -s -a
```  
## 新增 Ubuntu 螢幕解析度設定中未出現的項目
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
## 啟用終端機顯示顏色
將 ~/.bashrc 檔案中將 #force_color_prompt=yes 註解符號 # 刪除後，重新進入終端機

## 在 Ubuntu 中停用 IPv6 功能
編輯 /etc/sysctl.conf，在檔案最後加上以下內容後，
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
執行以下指令即可 
```bash
sudo sysctl -p
```

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
