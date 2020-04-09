# 第二天，vim 基本使用
## vim是啥
一款终端的文本编辑软件，功能类似于记事本或sublime text

## 快速开始
```
# 编辑 a.txt，如果不存在将新建
vim a.txt

# 按下i，进入编辑模式（即按键触发功能，而是输入字符，左下角会显示成 INSERT）
i

# 随便输入些内容，如果输错了
123

# 按esc退出编辑模式，进入到命令模式（即按键不会当成字符输入到文本中，而是作为命令，左下角 INSERT 字样会消失）
# 保存并退出，w - 保存，q - 退出
:wq

# 不保存，强制退出。不会保存自上次保存以来的改动，如果文件不存在不会新建文件
:q!
```

## 阅读文档
[简明 vim 练级攻略](https://coolshell.cn/articles/5426.html)

## 练习作业
新建 sort.py，输入以下代码：
```
def bubble_sorted(iterable):
    new_list = list(iterable)
    list_len = len(new_list)
    for i in range(list_len):
        for j in range(list_len - i - 1):
            if new_list[j] > new_list[j + 1]:
                new_list[j], new_list[j + 1] = new_list[j + 1], new_list[j]
    return new_list
```

尝试用到以下命令：
```
h、j、k、l：代替方向键来进行移动

0：跳到行首
$：跳到行未
w：跳到下一个单词

i：在光标前插入
I：在行首插入
a：在光标后插入
A：在行未插入

o：在当前行下面新建一行进行编辑
O：在当前行上面新建一行进行编辑

dw：删除一整个单词
d$：删除从当前光标到行未的内容
d0：删除从当前光标到行首的内容
dd：删除整行
10 dd：删除10行

p：粘贴（上一次删除或复制的内容）
P：粘贴到上面
u：撤销上一次命令

y：复制
yw：复制一个单词
yy：复制整行
y0、y$类似

gg：跳到第一行
G：跳到最后一行
:10：跳到第10行

/：搜索内容
```