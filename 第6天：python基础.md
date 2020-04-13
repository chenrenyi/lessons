# 第6天，python基础

## 快速开始
### hello world
vim 新建个 hello.py，内容如下：
```python
print("hello, world!")
```

运行程序：
```
python3 hello.py
```

### 加法器
稍微复杂点的例子`add.py`，实现一个加法器：
```python
a = 123
b = 456

def add(a, b):
    c = a + b
    return c

print(add(a, b))
```

运行程序看看：
```
python3 test.py
```

要点：

1. Python是动态语言，不区分类型，所以定义变量直接 `a = 3` 即可
2. 定义函数用 `def`
3. 没有方括号 `{}`，行未没有分号 `;`，取而代之的是 `:` 和缩进（即行首有几个空格），所以缩进不对会报语法错误

### 交互式程序
直接输入 `python` ，不接任何参数，会进入一个交互式的终端，试试看吧

### 变量类型
按如下内容新建`test1.py`，并运行：

```python
# 井号开头表示注释
a = 1.2 # 浮点数
b = True # 布尔型，必须大写
c = "im string" # 字符串类型

# if 语句
if a > 1:
    print('a > 1')
elif a == 1:
    print('a == 1')
else:
    print('a <= 1')

# 取反语句 not
if not b:
    print('b is false')
else:
    print('b is true')

```

### 数组和对象
按如下内容新建`test2.py`，并运行：
```python
# 我是数组，python中叫list，官方译名 列表，其实跟 java、c、js中的数组一样
a = []
b = [1, 2, 3, 4]

# 数组长度
print(len(b))

# 取数组值，跟其它语言一样下标是从0开始的
print(b[1])

# 赋值
b[1] = 345
print(b)

# 追加和删除
a.append(123)
print(a)
a.pop()
print(a)

# 对象，python中叫dict，官译字典，跟java、c++中的map，js中的对象是一类东西
user = {'name': 'chenrneyi', 'age': 25, 'sex': 1}
print(user)
print(user['name'])
print(user['age'])
user.name = 'qer'
print(user)
user.phone = '150'
print(user['phone'])
```

### 循环
```python
# 从1到100
for i in range(100):
    print(i)

# range是个啥呢
print(range(5))

# 遍历list
a = [1, 2, 3]
for i in a:
    print(a)

# while
n = 99
while n > 0:
    n = n - 1
    print(n)
```

## 学习
看下面的教程，至少看到 ** 函数 ** 这一节
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017100774566304]()

## 作业
1、用Python写一个冒泡排序
