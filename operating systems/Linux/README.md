# linux
linux-related notes

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
