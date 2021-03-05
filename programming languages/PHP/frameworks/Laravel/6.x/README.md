# Laravel 6.x

- [Directory Structure](#directory-structure)
  - [The `app` Directory](#the-app-directory)
  - [The `bootstrap` Directory](#the-bootstrap-directory)
  - [The `config` Directory](#the-config-directory)
  - [The `database` Directory](#the-database-directory)
  - [The `public` Directory](#the-public-directory)
  - [The `resources` Directory](#the-resources-directory)
  - [The `routes` Directory](#the-routes-directory)
  - [The `storage` Directory](#the-storage-directory)
  - [The `tests` Directory](#the-tests-directory)
  - [The `vendor` Directory](#the-vendor-directory)
- [Notes](#notes)

## Directory Structure

### The `app` Directory

程式中大部分 class 都會在這裡。使用 `php artisan make:model` 指令產生的 Eloquent ORM model 預設路徑也在此。可在指令的 class 名稱前加上 `Models/` 以指定路徑至 `app/Models/`

### The `bootstrap` Directory

包含框架的引導程式 `app.php`，以及框架產生的快取檔

### The `config` Directory

專案的各種參數設定

### The `database` Directory

包含資料庫的 `migration`、`model factory` (產生隨機資料)、`seeder` (預設資料)

### The `public` Directory

包含 `index.php` 以及圖片、JS、CSS 檔

### The `resources` Directory

包含未編譯的原始 JavaScript、SASS、LESS 等檔案，以及**語系檔**

### The `routes` Directory

* web.php：
* api.php：無狀態(使用 token 驗證，不使用 session)、可設定頻率限制
* console.php：
* channel.php：註冊事件廣播的頻道

### The `storage` Directory

包含已編譯的 blade 樣板、基於檔案的 session、檔案快取、其他由框架產生的檔案

子資料夾：
* app：程式產生的檔案
* framework：框架產生的檔案與快取
* logs：紀錄檔

`storage/app/public` 儲存由使用者產生可被公開存取的檔案，應使用 `php artisan storage:link` 指令將 `public/storage` 連結指向此路徑

### The `tests` Directory

自動化測試檔案，所有測試類別名稱應以 `Test` 結尾

### The `vendor` Directory

包含 Composer 的依賴檔案

## Notes

* 在測試中使用 `dump()` 有機會產生非預期的錯誤
