# 第4天，MySQL

## 安装 MySQL
Linux 下安装软件的一般方法：

1. 百度或谷歌 Ubuntu/Centos/xxx 安装 xxx
2. 按照搜索结果照做就行

比如搜索：如何安装：直接百度 ubuntu 安装 MySQL

得到结果：

[https://blog.csdn.net/weixx3/article/details/80782479]()

## 使用 MySQL
### 基本概念
使用需要账户和密码，默认的也是权限最高的账户是root

权限有以下几种：

1、能访问哪些数据库和哪些表

2、只读、还是可以写入更新数据，甚至可以创建表和修改表结构

3、能从哪些ip登录，比如只能从本地登录，只能从某个ip段登录，或者无限制

### 语法
DDL：Data Definition Language，修改表结构的
```MySQL
CREATE
ALTER
DROP
TRUNCATE
RENAME
```
DML（Data Manipulation Language），修改表数据的
```MySQL
SELECT
INSERT
UPDATE
DELETE
```

## 练习
### 登录进MySQL
登录

### 创建数据库
取名为 qerdb
> 一个MySQL服务，可以有多个数据库（database）
> 
> 一个数据库(database)下面，可以有多个表(table)

### 创建两个表
1、查看当前有哪些数据库

2、进入数据库 qerdb

3、查看当前数据库有哪些表 

4、创建两个表
> 假设有个博客网站，有用户在上面发表博客，我们需要存储用户和博客信息

创建用户表，取名user，有以下字段：

| 字段 | 类型 | 备注 |
| --- | --- | --- |
| id |  int | 主键ID |
| name |  varchar | 姓名 |
| age |  int | 年龄 |

创建博客表，取名blog，有以下字段：

| 字段 | 类型 | 备注 |
| --- | --- | --- |
| id |  int | 主键ID |
| user_id | int | 作者的用户ID |
| title | varchar | 标题 |

### 查看表
1、查看现在有哪些表

2、查看 user 表的结构

3、显示 blog 表的创建语句

### 输入数据
user表，内容如下：

| id | 姓名 | 年龄 |
| --- | --- | --- |
| 1 | hanhan | 34 |
| 2 | bob | 18 |
| 3 | lili | 22 |
| 4 | toy | 5 |
| 5 | jack | 22 |
| 6 | cat | 20 |

blog表，内容如下：

| id | 作者ID | 标题 |
| --- | --- | --- |
| 1 | 2 | haha |
| 2 | 3 | yes |
| 3 | 3 | good |
| 4 | 5 | no |
| 5 | 5 | ok |
| 6 | 3 | nice |

尝试一次插入一条，与一次插入多条数据

### 查询数据

### 创建索引

### 导入与导出数据

## 答案
```MySQL
# 创建数据库
CREATE DATABASE `qerdb` DEFAULT CHARACTER SET = `utf8mb4`;
SHOW DATABASES;
USE `qerdb`;
SHOW tables;
```

```MySQL
# 用户表
CREATE TABLE `user` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT 'ID',
  `name` varchar(255) DEFAULT NULL COMMENT '姓名',
  `age` smallint(11) DEFAULT NULL COMMENT '年龄',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='用户表';

# 博客表
CREATE TABLE `blog` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `user_id` int(11) NOT NULL COMMENT '文章作者ID',
  `title` varchar(255) NOT NULL DEFAULT '' COMMENT '文章标题',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='博客表';

SHOW tables;
DESC user;
SHOW CREATE TABLE user;
```

```MySQL
# 输入数据
INSERT INTO `user` (`id`, `name`, `age`) VALUES (NULL, 'hanhan', '34');
INSERT INTO `user` (`id`, `name`, `age`) VALUES (NULL, 'bob', '18');

INSERT INTO `user` (`id`, `name`, `age`)
VALUES
    (3,'lili',22),
    (4,'toy',5),
    (5,'jack',22),
    (6,'cat',20);


INSERT INTO `blog` (`id`, `user_id`, `title`)
VALUES
    (1,2,'haha'),
    (2,3,'yes'),
    (3,3,'good'),
    (4,5,'no'),
    (5,5,'ok'),
    (6,3,'nice');
```
