# 第5天，git
## 介绍
版本控制软件，实际工作中主要作用如下：

1. 用来提交代码到服务器上，和从服务器上下载代码
> 对公司来说，代码需要保存在一个公共的服务器上，放在个人电脑上容易丢失且不安全
2. 用来分工协作。
> 大家各自开发，然后各自提交代码到git服务器和下载，不用在QQ上发送文件了
> 
> 假如两个人修改了同一份文件，git会自动检测到冲突，提醒人去处理
> 
3. 用来做版本控制
> 可以保存每次的修改版本，方便回滚回去
> 
> 可以通过日志查看出，谁在某个时间点，某一次修改中，改了哪些文件的哪些行。方便排查问题。
> 
> 有分支管理功能，可以同时开多个分支，在不同分支上开发不同功能
> 

## github
是一个基于 git 的网站，相当于在服务端 git 的基础上面，加了可视化的功能。

同时提供了一些额外的方便功能，比如评论系统等等

主要场景：

1. 开源软件把代码托管在上面，供大家查看、报bug。或者热心人员开发代码提交，然后让开源软件管理者合入进去，从而实现共同开发
2. 公司付费，用github来管理自己的代码库

## 参考文档

[https://www.jianshu.com/p/296d22275cdd]()

## 重点学会
1、知道如何创建仓库、添加文件、提交、上传、下载，即：

* git init
* git add/rm
* git commit
* git push 
* git pull

2、了解下回滚，分支，撤销添加文件

## 作业
注册一个 github账户，并在里面提交一个项目

