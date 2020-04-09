# 第一天，学习Linux基本使用
## 连接到Linux服务器

    ssh 用户名@服务器地址

>类似于远程桌面，输入密码后继续，输入时密码不可见

## 随便看看
成功登录后，尝试下以下命令

    pwd     查看当前所在目录
    ls      查看当前目录下有哪些文件
    cd ..   进入到上级目录

## 阅读文档
[Linux基础](https://linuxtools-rst.readthedocs.io/zh_CN/latest/base/01_use_man.html)

> 第一二节必看
> 
> 第三节必看 grep，看下 find，其它选看
> 
> 第五节，了解下 ps、lsof -i:端口，kill，top，知道用途即可，无需记住参数
> 
> 其它节可以过下

## 练习
1、创建 `pratice` 目录，并进入该目录

2、创建 `tmp`, `test` 两个目录

3、重命名 `test` 目录为 `site`，并进入该目录

4、创建一个名为 `index.html` 的空白文件
>提示：可用命令touch

5、创建一个名为 `app.js` 的文件，并输入内容 `123`，然后追回内容`456`。打印 `app.js` 的内容
> 提示：可用命令 echo，结合管道符号 `>>`

6、复制 `app.js` 为 `app2.js`，打印 `app2.js` 的全部内容、第一行内容、最后一行内容

7、输出 `app2.js` 中包含字符串 `123` 的行内容

8、查看当前目录下有哪些文件和目录。查看当前目录下以 `.html` 结尾的所有文件名

9、查看当前所在目录，切换到上一级目录，然后查看该目录下内容，查看该目录下的子目录 `site` 的内容。删除子目录 `site`

10、回到家目录

11、输出字符串 "I'm great"

## 答案
```
# 1
mkdir pratice
cd pratice

# 2
mkdir tmp
mkdir test

# 3
mv test site
cd site

# 4
touch index.html

# 5
echo "123" >> app.js
echo "456" >> app.js
cat app.js

# 6
cp app.js app2.js
cat app2.js
head -n 1 app2.js
tail -n 1 app2.js

# 7
cat app2.js | grep "123"

# 8
ls
ls | grep ".html"

# 9
pwd
cd ..
ls
ls site/
rm -rf site

# 10
cd

# 11
echo "I'm great"
```


## 扩展阅读
[shell脚本](https://github.com/qinjx/30min_guides/blob/master/shell.md)
