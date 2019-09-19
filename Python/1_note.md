# 笔记
# -1. 网络教程
http://www.runoob.com/python/python-install.html

网页：[只需十四步：从零开始掌握 Python 机器学习（附资源）](https://www.cnblogs.com/aabbcc/p/8683042.html)

视屏教学：[机器学习](https://www.coursera.org/learn/machine-learning)

## 编译器
mac系统自带，`python --version`查看版本号
运行两种方式：
1. 输入`python`后进入提示符操作
2. 写入脚本中，扩展名`.py`，执行方式：`python file.py`

### hello world
```python
# hello.py
print('hello world')
```

## 特殊格式

* 注释：`#`右边的都是注释
* 续行：`\`，如果有使用括号，默认是续行的
* 缩进用来决定逻辑层次，非常重要。缩进数量必须始终一致，否则报错：IndentationError
* 一行可以写多条语句，用分号隔开

## 变量

* 变量名开头：大小写字母，下划线
* 变量名组成：大小写字母，下划线，数字
* 大小写敏感
* 不需要定义类型

### 五个标准的数据类型：

Numbers（数字）
String（字符串）
List（列表）
Tuple（元组）
Dictionary（字典）

### 下划线开头变量

* 单下划线开头：不能直接访问的类属性，不能用`from xxx import *`导入。需要通过类提供的接口访问，如`_foo`
* 双下划线开头：类的私有成员，如`__foo`
* 双下划线开头和结尾：python里特殊方法专用的标识，如`__int__()`代表类的构造函数

### 支持的数字类型
int（整型）
~~long（长整型[也可以代表八进制和十六进制]，`51924361L，0xABCL`）~~(python 3中long型被移除。如果数据过长int会自动转为long）
float（浮点型`3.2, 3.2E-2`）
complex（复数`-5+4j`）

### 基本操作
#### 定义与调用

```python
counter = 100 # 赋值整型变量
counter = counter + 1
miles = 1000.0 # 浮点型
name = "John" # 字符串
```

##### 多个变量赋值

多个变量可以放在一起赋值：

```python
a=b=c=1
a, b, c = 1, 2, 'abc'
```

#### 运算
类别 | 符号
--- | ---
四则运算 | `+,-,*,/`
幂 | `**`
取整除 | `//`，去掉小数
取模 | `%`
比较大小 | `>, >=, <, <=, ==, !=`
非 | `not`
与 | `and`
或 | `or`


### 列表
创建：`list = ['aa','bb']`
追加：`list.append('cc')`
长度：`len(list)`
调用全部：`list`
调用第一个：`list[0]`
删除：`del list[1]`
排序：`list.sort()`

### 字符串
单引号或双引号，单（双）引号中自动忽略双（单）引号
三个单（双）引号，表示多行的字符串，内容中可以自由使用单/双引号
转义字符`\`可以屏蔽下一个引号，或者连接两行内容为一个字符串

```python
print "I'd much 'not',"
print 'I\'d much '
print 'I "said" do not touch this'
print '''This is first line
second line 'hello'
third line "hello"
'''
```

字符串有两种取值顺序（N为字符个数）：
从左往右，0开始，到N-1
从右往左，-1开始，到-N

自然字符串：不要采用任何转义去解释，加上前缀`r`或`R`表示：`r'do \n'`
**注意**：
* 两个字符串会自动拼接
* 字符串定义后不可改变
* 长度：`len(str)`
* 连接：`str1 += str2`
* 比较：`cmp(sStr1,sStr2)`
* 截取：`print str[0:3]`

## 逻辑
### 非
### 判断if

最简单的if语句:

```python
if True:	print 'Yes, it is true'
```

一个if-elif-else例子，注意最后的那句每次都会执行

```python
# Filename: if.pynumber = 23guess = int(raw_input('Enter an integer : '))
if guess == number:	print 'Congratulations, you guessed it.' elif guess < number:	print 'No, it is a little higher than that' else:	print 'No, it is a little lower than that'print 'Done'# This last statement is always executed, after the if statement is executed
```

### while循环
```python
number = 23 
running = Truewhile running:	guess = int(raw_input('Enter an integer : '))	if guess == number:		print 'Congratulations, you guessed it.'		running = False # this causes the while loop to stop	elif guess < number:		print 'No, it is a little higher than that'	else:		print 'No, it is a little lower than that'else:	print 'The while loop is over.'	# Do anything else you want to do hereprint 'Done'
```
### for循环
```pythonfor i in range(1, 5): 
	print ielse:	print 'The for loop is over'
```
### 循环控制
break会跳出for与while循环，并且不执行else中的语句
continue会提前进入下一次for与while循环
## 函数
关键字`def`定义，变量传递的是形参。通过缩进结束。return是返回值，默认返回`return None`

```pythondef printMax(a, b): 
	if a > b:		print a, 'is maximum' 
		return a
	else:		print b, 'is maximum'
		return b
	printMax(3, 4) # directly give literal values
```
### 全局变量
函数默认是局部变量，如果要声明全局变量，需要关键字`global`
同时声明多个全局变量，`global x,y,z`

```python
def func(): 
	global x
		print 'x is', x	x= 2	print 'Changed local x to', x
	x = 50func()print 'Value of x is', x
```

### 设定参数预设值
参数的个数是可选的，缺省的参数预先在定义时用`=`设定。预设的参数只能放在后面。

```python
def say(message, times = 1): 
	print message * timessay('Hello') 
say('World', 5)
```
### 打乱顺序赋值
函数调用时，指定变量名称可以不按顺序赋值。这种方法可以结合上面的”预设参数值“使用

```python
def func(a, b=5, c=10):	print 'a is', a, 'and b is', b, 'and c is', c
	func(3, 7) 
func(25, c=24) 
func(c=50, a=100)
```
### 函数帮助文档
函数开头用三个引号引起来的内容为帮助文档，通过其类`.__doc__`可以调用，用帮助函数help(fun_name)也是调用这个内容。

```python
def printMax(x, y):	'''Prints the maximum of two numbers.	The two values must be integers.'''	x = int(x) # convert to integers, if possible y = int(y)	if x > y:		print x, 'is maximum'	else:		print y, 'is maximum'printMax(3, 5)print printMax.__doc__
```

## 模块
用`import modulename`调用，会在系统路径下查找`modulename.py`
为了使调用更快，可以使用字节编译的`.pyc`文件，这个文件也是与平台无关的。

### 调用sys模块
这里调用一个很常见的`sys`模块，`.argv`表示文件名（argv[0]），输入变量（从argv[1]开始）

```python
import sys                                                                      
print 'The command line arguments are:'

for i in sys.argv:
  print i

print '\n\n The path are', sys.path,'\n'
```
为了避免每次都打sys，可以把sys的变量导入到自己的程序中
导入argv：`from sys import argv`
导入所有：`from sys import *`
但是这种用法慎用，会使代码更易读，并避免名称冲突
### 定义自己的模块
#### 定义
定义了一个函数和一个变量

```python
#!/usr/bin/python# Filename: mymodule.pydef sayhi():	print 'Hi, this is mymodule speaking.'
	version = '0.1'# End of mymodule.py
```
#### 调用

```python
#!/usr/bin/python# Filename: mymodule_demo.py
import mymodulemymodule.sayhi()print 'Version', mymodule.version
```
输出：

```python$ python mymodule_demo.py 
Hi, this is mymodule speaking. 
Version 0.1
```
## 内建函数
len：长度
range：range(1,5)返回1，2，3，4；range(1,5,2)返回1,3
pass：空语句
## 输入输出
### 输入

```python
a=input('input the value of a\n')
```

### 输出
```python
length = 5breadth = 2area = length * breadthprint 'Area is', areaprint 'Perimeter is', 2 * (length + breadth)
```
注意：字符串后面接变量时，输出会自动用空格隔开


