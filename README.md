# 此範例為 **倉庫系統 (Warehouse Management System, WMS)** 的使用者資料表，主要用於儲存系統使用者的基本資訊與角色設定。

此範例為 MySQL** WMS02 使用者資料表

## 建表與測試資料

```sql
-- 建表語法

-- 欄位說明
-- id       : 主鍵，自動遞增
-- no       : 帳號（例如員工編號、登入帳號）
-- name     : 姓名
-- password : 密碼（建議實務上使用雜湊加密，不要存明碼）
-- age      : 年齡
-- sex      : 性別（建議定義 0=女，1=男）
-- phone    : 電話
-- role_id  : 角色（0=超管、1=管理員、2=一般帳號）
-- isvalid  : 是否有效（預設 Y=有效，其他=無效）
```
```
## 測試資料

測試會員說明:
超級管理員 (sa)
擁有最高權限，可以管理所有使用者與系統配置。
role_id = 0 → 代表超級管理員角色。

管理員 (admin01)
負責日常系統管理，例如維護倉庫資訊、管理一般會員。
role_id = 1 → 代表管理員角色。

普通會員 (user01)
一般使用者，主要用於倉庫操作（如查詢庫存、建立訂單）。
role_id = 2 → 代表普通帳號角色。
```  
## Spring Boot 的 應用程式設定檔（可以是 application.yml 或 application.properties）
```
spring.datasource
```
這一段是 資料庫連線設定，告訴 Spring Boot 要怎麼連到 MySQL。


```
jdbc:mysql://localhost:3306/wms02?useUnicode=true&characterEncoding=utf-8&useSSL=false&serverTimezone=Asia/Taipei
```
拆解：

jdbc:mysql:// → 告訴 Java 要用 MySQL 協議。

localhost:3306 → MySQL 伺服器在本機 (localhost)，使用預設埠號 3306。

wms02 → 你要連的資料庫名稱。

useUnicode=true&characterEncoding=utf-8 → 避免中文亂碼。

useSSL=false → 不使用 SSL，否則會跳警告。

serverTimezone=Asia/Taipei → 設定時區，避免時間錯誤。
