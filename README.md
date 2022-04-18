sql-study
----------

野生笔记，参考：
1. SQL初学者教程
2. SQL数据分析 轻松学习（对比Excel）
3. MICK的SQL基础教程、进阶教程
4. 技术面试必备基础知识 CyC2018 的 sql和数据库知识 部分
5. [SQL 教程 | 菜鸟教程](https://www.runoob.com/sql/sql-tutorial.html)
6. [SQL教程（从入门到精通）](http://c.biancheng.net/sql/)

> 只记录sql使用方法，不记录可视化界面的使用方法（因为各UI的使用都不尽相同）

# 1. 搭建mysql环境
1. 安装docker engine（linux） 或 docker desktop（windows/macOS）
2. 下载本仓库的`docker-compose.yml`文件，同目录下 运行 `docker-compose up -d` 命令，完成启动
   - 后端为mysql
   - 前端为[adminer](https://www.adminer.org/)
3. 可视化编程：访问 [http://localhost:8080](http://localhost:8080), 使用用户名 `root` 密码`exmaple` 登陆
   ![mysql_adminer](https://images.weserv.nl?url=https://raw.githubusercontent.com/dennischancs/pic/main/img/202204181105699.png)
   ![sql命令界面](https://images.weserv.nl?url=https://raw.githubusercontent.com/dennischancs/pic/main/img/202204181133140.png)
4. 若要使用其它可视化编程界面，填写相应`ipaddress:port@usr/passwd`连接。以navicat为例
   ![navicat](https://images.weserv.nl?url=https://raw.githubusercontent.com/dennischancs/pic/main/img/202204181135190.png)

# SQL语句种类与SQL语句构成

## SQL语句种类

 种类 | 简介 | 可操作对象 | 指令（增删改查）
-----|------|---------|-----
 DDL| data definition language 数据定义语言 | 数据库、数据库中的表 | create创建 / drop删除 / alter更改结构
 DML| data manipulation language 数据操纵语言 | 数据库中的表 | select查询表中数据 / insert表中插入新数据 / update更新表中数据 / delete删除表中数据
 DCL | data control language 数据控制语言 | 动作确认（确认或取消对数据库中的数据进行的变更）、 赋权（赋予与取消用户操作权限）| commit确认变更 / rollback回滚取消变更 / grant赋予权限 / revoke取消权限

注：实际使用的SQL语句当中有90%属于DML。

## SQL语句的构成：`关键字(大写)、表名、列名`

> 一个好习惯：关键字使用大写，表名、列名使用小写。使代码便于阅读。

```sql
CREATE DATABASE study;  -- 创建了一个名称是study的数据库
USE study;              -- 使用study数据库

CREATE TABLE Persons    -- 创建了一个名称是Persons的数据表
(
PersonID int,           -- 第1列，列名是PersonID，数据类型是int
LastName varchar(255),  -- 第2列，列名是LastName，数据类型是可变长度字符串（最大长度为255个字符）
FirstName varchar(255),
Address varchar(255),
City varchar(255)
);

CREATE TABLE website (  -- 创建了一个名称是website的数据表
    id      INT              NOT NULL   AUTO_INCREMENT,  -- 第1列，列名是id，数据类型是int，AUTO_INCREMENT约束 指定 该字段的值为自动增长的序列
    name    VARCHAR(20)      NOT NULL,                   -- 第2列，列名是name，数据类型是可变长度字符串（最大长度为20个字符）
    url     VARCHAR(30)                 DEFAULT '',      -- DEFAULT约束 指定 该字段的默认值，此处默认值留空
    age     TINYINT UNSIGNED NOT NULL,                   -- NOT NULL约束 指定 表名在插入数据时这些字段不能为 NULL
    alexa   INT UNSIGNED     NOT NULL,
    uv      FLOAT                       DEFAULT '0',     -- DEFAULT约束 指定 该字段的默认值，此处默认值为0
    country CHAR(3)          NOT NULL   DEFAULT '',
    PRIMARY KEY (`id`)  -- 设置表的主键为 id (第1列的列名)
);

DESC website                            -- description查看表的信息描述，可用于验证 website 表是否存在
DESC Persons
SELECT * FROM Persons                   -- 展示Persons表中的数据
SELECT * FROM Persons WHERE LastName='dennis'  -- 字符串必须加''
DELETE FROM Persons WHERE PersonID=1    -- 删除Persons表中 PersonID列中 值为`1`的行，`PersonID=1`为真值时才会执行`DELETE`指令
DELETE FROM Persons WHERE PersonID='1'  -- 数值加不加''均可
TRUNCATE TABLE Persons                  -- 清空Persons表中的数据
DROP TABLE website, Persons             -- 删除website, Persons 表（在study数据库中）
DROP DATABASE study                     -- 删除study数据库

```





# 2. sql核心命令
<!-- 第2章 -->

# 3. sql查询与集合运算
<!-- 第3章 -->
<!-- 第6章 -->

# 4. sql聚合查询（类似excel数据透视表）
<!-- 第4章 -->

# 5. 函数与条件语句( 布尔运算/谓词 与 条件语句/case流程控制 )
<!-- 第5章 -->

# 6. 窗口函数
<!-- 第7章 -->