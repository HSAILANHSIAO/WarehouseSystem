# WMS02 使用者資料表

此範例為 **倉庫系統 (Warehouse Management System, WMS)** 的使用者資料表，主要用於儲存系統使用者的基本資訊與角色設定。

## 建表與測試資料

```sql
-- 建表語法
CREATE TABLE user (
    id INT AUTO_INCREMENT PRIMARY KEY COMMENT '主鍵',
    no VARCHAR(20) NULL COMMENT '帳號',
    name VARCHAR(100) NOT NULL COMMENT '名字',
    password VARCHAR(20) NOT NULL COMMENT '密碼',
    age INT NULL COMMENT '年齡',
    sex INT NULL COMMENT '性別',
    phone VARCHAR(20) NULL COMMENT '電話',
    role_id INT NULL COMMENT '角色 (0=超級管理員, 1=管理員, 2=普通帳號)',
    isvalid VARCHAR(4) DEFAULT 'Y' NULL COMMENT '是否有效，Y有效，其他無效'
) CHARACTER SET = utf8;
```


```
-- 測試資料

-- 超級管理員
INSERT INTO user (no, name, password, age, sex, phone, role_id, isvalid)
VALUES ('sa', '超級管理員', '123', 18, 1, '111', 0, 'Y');

-- 管理員
INSERT INTO user (no, name, password, age, sex, phone, role_id, isvalid)
VALUES ('admin01', '系統管理員', 'admin123', 30, 1, '0911222333', 1, 'Y');

-- 普通帳號
INSERT INTO user (no, name, password, age, sex, phone, role_id, isvalid)
VALUES ('user01', '王小明', 'userpwd', 25, 0, '0922333444', 2, 'Y');

```

測試會員說明

超級管理員 (sa)
擁有最高權限，可以管理所有使用者與系統配置。
role_id = 0 → 代表超級管理員角色。

管理員 (admin01)
負責日常系統管理，例如維護倉庫資訊、管理一般會員。
role_id = 1 → 代表管理員角色。

普通會員 (user01)
一般使用者，主要用於倉庫操作（如查詢庫存、建立訂單）。
role_id = 2 → 代表普通帳號角色。
