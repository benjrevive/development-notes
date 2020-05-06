# windows-notes

## Batch
### 暫停特定秒數
```batch
timeout /t 5
```

### 傳入引數
其中一種做法：
```batch
:loop
IF NOT "%1"=="" (
    IF "%1"=="-arg1" (
        SET var1=%2
        SHIFT
    ) ELSE IF "%1"=="-arg2" (
        SET var2=%2
        SHIFT
    )
    SHIFT
    GOTO:loop
)
```

## Others
### 避免 Win10 更新後自動重新開機

目標路徑: `C:\Windows\System32\Tasks\Microsoft\Windows\UpdateOrchestrator\`

將檔案 `Reboot` (或 `Reboot_AC` 與 `Reboot_Battery`) 重新命名為 `Reboot.bak` (`Reboot_AC.bak`, etc.) 或類似可分辨名稱，並新增與原檔名同名之資料夾(`Reboot`, `Reboot_AC`, etc.)取代之，使系統無法執行更新後之重新開機程序。

> ref: *停止Win10 自動重新開機 - TOMMYHSU.com http://tommyhsu.com/archives/236037*
