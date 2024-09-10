### 默认导出

`mysqldump database --column-statistics=0 --result-file="D:\\sql\\{data_source}-{database}-{timestamp}.sql"`

### 忽略gtid导出

`mysqldump database --column-statistics=0 --set-gtid-purged=OFF --result-file="D:\\sql\\{data_source}-{database}-{timestamp}.sql"`

### 导出event和routines

`mysqldump database --column-statistics=0 --set-gtid-purged=OFF --events --routines --result-file="D:\\sql\\{data_source}-{database}-{timestamp}.sql"`

### 导入

`mysql -u root -p database < xxx.sql`

### 以uft8导入

`mysql -u root -p database < xx.sql --default-character-set=utf8`

`mysql -u root -p eopdb < 192_168_166_84-eopdb-2024_01_24_13_43_49.sql --default-character-set=utf8`
`mysql -u root -p eoplogdb <`

<span>
-d 结构(--no-data:不导出任何数据，只导出数据库表结构)
-t 数据(--no-create-info:只导出数据，而不添加CREATE TABLE 语句)
-n (--no-create-db:只导出数据，而不添加CREATE DATABASE 语句）
-R (--routines:导出存储过程以及自定义函数)
-E (--events:导出事件)
--triggers (默认导出触发器，使用--skip-triggers屏蔽导出)
-B (--databases:导出数据库列表，单个库时可省略）
--tables 表列表（单个表时可省略）
①同时导出结构以及数据时可同时省略-d和-t
②同时 不 导出结构和数据可使用-ntd
③只导出存储过程和函数可使用-R -ntd
④导出所有(结构&数据&存储过程&函数&事件&触发器)使用-R -E(相当于①，省略了-d -t;触发器默认导出)
⑤只导出结构&函数&事件&触发器使用 -R -E -d
</span>
