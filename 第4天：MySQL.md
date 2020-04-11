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

### 参考文档
百度 谷歌 MySQL教程，比如得到结果：

[https://www.runoob.com/mysql/mysql-tutorial.html]()

## 练习
### 登录进MySQL
登录

### 创建数据库
创建一个数据库并取名为 qerdb
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
1、查询总的博客数量

2、查询并显示如下信息：博客标题、作者姓名

3、查询出所有人的年龄和

4、查询出用户中最大的年龄

5、查询出年龄第二大和第三大的两个用户

6、按年龄顺序从小到大显示所有用户

7、查询出没写过任何博客的用户数量

8、查询出写过博客的用户数量

9、查询并显示如下信息：人名，博客数量

10、按写的博客数量大到小显示人名

### 修改数据

1、把所有人的年龄加1

2、删掉用户 cat

3、把年龄小于20的的人的年龄减1

4、把姓名中含有字母o的人的年龄加1

### DDL
1、给blog表的user_id字段添加索引（顺便了解下唯一索引）

2、查看blog表的表结构、表创建语句有什么变化

3、给blog表，添加一个字段content

4、将 blog 表字段 id 的类型，修改为 bigint

### 导入与导出数据
1、导出 user 表的全部数据

2、新建一张与user一样的表，取名为user_back，并导入刚刚导出的数据

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

```MySQL
# 查询数据
# 1
select count(*) from blog;

# 2
select blog.title, user.name from blog, user where blog.user_id = user.id;

# 3
select sum(age) from user;

# 4
select max(age) from user;

# 5
select * from user order by age desc limit 1, 2;

# 6
select * from user order by age;

# 7
select count(*) from user where not exists(select 1 from blog where blog.user_id = user.id);
select count(*) from user left join blog on user.id = blog.user_id where blog.id is null;

# 8
select count(*) from user where exists(select 1 from blog where blog.user_id = user.id);
select count(*) from user left join blog on user.id = blog.user_id where blog.id is not null;
select count(distinct(user_id)) from blog;

# 9
select user.name, count(1) from user, blog where user.id = blog.user_id group by blog.user_id;

# 10
select user.name, count(1) as blog_count from user, blog where user.id = blog.user_id group by blog.user_id order by blog_count desc;
select name from user where id in (select user_id from blog group by user_id order by count(*) );
```

```MySQL
# 修改数据
update user set age = age + 1;

delete from user where name = "cat"

update user set age = age - 1 where age < 20;

update user set age = age + 1 where name like '%o%';
```

```MySQL
# 创建索引
ALTER TABLE `blog` ADD INDEX (`user_id`);
DESC blog;
show create table blog;

# 添加字段
ALTER TABLE `blog` ADD `content` VARCHAR(1024)  NOT NULL  DEFAULT ''  COMMENT '内容'  AFTER `title`;

# 修改字段类型
ALTER TABLE `blog` CHANGE `id` `id` BIGINT(11)  UNSIGNED  NOT NULL  AUTO_INCREMENT;
```

```MySQL
# 导入与导出
mysqldump 命令

source 命令
```

