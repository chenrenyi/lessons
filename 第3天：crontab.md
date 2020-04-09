# 第三天，crontab

## 快速开始
crontab是一个系统预装的程序，用来执行定时任务：比如每天1点跑个监控任务，每天中午发个汇总邮件，每天清理下文件，每分钟执行一些数据同步任务等等
```
crontab -l：打印的定时任务

crontab -e：新增/修改定时任务
```

## 语法
```
# 时间周期 命令
# 以下即每分钟创建一个 /tmp/123.txt
* * * * * touch /tmp/123.txt
```

## 命令
就是普通的 Linux命令

## 阅读文档
[参考文档](https://www.runoob.com/linux/linux-comm-crontab.html)

[在线生成工具](http://cron.qqe2.com/)

## 作业
建一个定时任务，每分钟在 /tmp 下生成一个 123.txt

