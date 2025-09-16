# WMS02 使用者資料表

此範例為 **倉庫系統 (Warehouse Management System, WMS)** 的使用者資料表，主要用於儲存系統使用者的基本資訊與角色設定。

```sql
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
