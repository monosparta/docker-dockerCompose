# Docker Compose 實作

## 安裝

### Windows、Mac
  
Docker compose已被包含於Docker Desktop中，無須特別安裝。

### Linux

先決條件：**需要事先安裝Docker Engine**

``` code=bash
<!-- 下載目前穩定版本的 Docker Compose -->
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
<!-- 設定檔案權限並執行 -->
$ sudo chmod +x /usr/local/bin/docker-compose
<!-- 測試 docker compose -->
$ docker-compose --version
```

:warning: 若 docker-compose 指令失敗，檢查路徑，創建象徵性連結(symbolic link)至 usr/bin

```code=bash
<!-- 創建連結 -->
$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

## 實作

[魏子靖-Docker Compose – 安裝教學、指令用法及官方範例說明](https://www.jinnsblog.com/2020/12/docker-compose-tutorial.html)

``` code=bash
<!-- 常用指令 -->
$ docker-compose up -d
$ docker-compose stop
$ docker-compose rm
```
