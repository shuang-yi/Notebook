SHELL快速参考
# 0. 基本格式

* 多条代码位于同一行：`;`隔开
* 一条代码跨行：`\`
* `#`注释


# 1. 变量
## 定义
赋值：`var=$var2`
删除：`unset var`
## 计算

```bash
((i++))  # each round i is increased by 1

((i=$j+$k))    
i=`expr $j + $k` #等价于上式，注意expr中加号两边的空格

var=$(( 20 + 5 ))
s=$[s+t] 

c=$(echo "5.01-4*2.0"|bc) #浮点数计算

```

## 数组
- 声明
	
```bash
array[0]=one
array[1]=two
array=( value1 value2 value3 ... )
array=( `seq 10` ) # start from 1
```
- 访问
	
```bash
${array[0]} # 第1个
${array[*]:i:n} # 从第i个开始，一共n个（返回空格隔开的字符串，外面再加小括号组成新数组）
${a[*]} #所有
```
- 删除
	
```bash
unset array[1] 
unset a[n-1]#删除第n个
unset a #删除所有
```
- 长度
	
```
${#array[*]}
```

### 保存文件名为数据

```bash
num=(`seq 0 5`) # the order can be rearranged
i=0
for file in `ls path/*txt`
do
  flist[${num[$i]}]=$file
  ((i++))
done
```
## 字符串
### 拼接
直接写在一起，有歧义的用大括号隔开：

```
${a}stringNew
```
#### 截取

```bash
${a,start,end} # start 为负表示右端第 start个， end可省
expr substr $str $start $length
expr match "$str" '\($pattern\)'
expr "$str" : '\($pattern\)'
```
#### 删除匹配部分
`${a#a*b}`     最短模式，从前端开始删除
`${a##a*b}`    最长模式，必须从前端开始删
`${a%a*b}`     后端开始删除，最短模式
`${a%%a*b}`    最长模式
`echo $a|cut –d: -f2` ：按照冒号分割，取第二份（起点为1）
### 长度

```
${#a}
```
### 替换

```bash
${a/str1/replace}  # 替换一次
${a//str1/replace} # 全部替换
${a/#str1/replace} # 前端匹配则替换
${a/%str1/replace} # 后端匹配则替换
```
### 查找

```
expr index "$string" $substring
从左端开始的在 string中的位置，起点 1
```
## 环境变量
变量 | 说明
---- | ----
USER | 已登录用户的用户名
UID | 已登录用户的数字用户 id
HOME | 用户的主目录
PWD | 当前工作目录
SHELL | shell 名
$ | 进程 id （或正在运行的 Bashshell进程或其他进程的 PID ）
PPID | 启动这个进程的进程的进程 id （即父进程的 id）
? | 上一个命令的退出码
0 | 文件名
${#*} | Number of command line parameters passed to script
${#@} | Number of command line parameters passed to script
$? | Return value
$$ | Process ID (PID) of script
$- | Flags passed to script (using set)
$_ | Last argument of previous command
$! | Process ID (PID) of last job run in background
# 2. 逻辑
## 条件格式
两种方式，注意第二种中括号两边必须带空格

```shell
test condition
[ condition ]
[ condition1 -a condition2 ]
```
## 比较
### 一般

```shell
! condition     # negates condition
cond1 -a cond2  # and
cond1 -o cond2  # or
\( \)           # group condition
```
### 整型

```shell
int1 -eq int2   # ==
int1 -ne int2   # !=
int1 -gt int2   # >
int1 -ge int2   # >=
int1 -lt int2   # <
int1 -le int2   # <=
```
### 字符串

```shell
str1 = str2     # equals
str1 != str2    # different
str1            # not null
-z string       # length is 0
-n string       # length > 0
```
### 文件

```shell
-s file     # file > 0 length
-r file     # readable
-w file     # writable
-x file     # executable
-f file     # exists and is a regular file
-d file     # directory; ! -d "$path", directory not exists
```

## if 判断
```bash
if condition
then
  commands
elif condition 
then
  xxx
else
  xxx
fi
```
## for 循环
包括多行和单行格式：

```bash
for ((i=0;i<=5;i++)); 
do 
    echo $(expr $i \* 4); 
done

for ~; do echo $File; done
```

For循环的第一行语句可以用下面的替换：

```bash
for i in $(seq 10)  	#序列
for i in `ls`			#文件列表
for i in ${arr[@]}	#字符串
for File in /proc/*	#文件列表
for i in f1 f2 f3		#变量列表
```
## while 循环

```bash
# 读取键盘输入
while [ "$str" != "yes" ]
do
	read -p "input yes:" str
done

# 读取文件
while read f
do 
    echo "Line is $f"
done < file 
```
## case条件

```bash
case string in
pattern1) # can be an integer or a single quoted string
xxx
;;

pattern2)
xxx
;;

*)  # default case
xxx
;;

esac
```
# 3. 函数

```bash
function fSum()
{
echo $1,$2;
return $(($1+$2));
}
fSum 5 7;
```
## 注意：
- 需要调用前声明

## 函数变量：

* `$@` ：所有变量，作为分离的字符串
* `"$*"` ：所有变量，作为一个字符串
* `#` ：变量个数
* `1-9` ：第1-9 个变量 ,${10}

# 4. 输入输出
## 读入键盘

```bash
read -p "input yes:" str
```
## 持续读取文件
``` bash
# method 1：依次按行读取
while read myline 
do
    echo "LINE:"$myline
done < datafile.txt

# method 2：得到一组文件名
for sfile in `ls *.txt`
do

done
```
## 读入一组文件成为数组：
方法1：

```
ARRAY=($(awk '{print $2}' ip.txt))
```
方法2：

```bash
n=0
while read b
do 
  array[$n]=$b
  ((n++))
done < ip.txt
```
方法3：

```bash
n=0
for x in ` awk '{print $2}' ip.txt `
do
    array[$n]=$x
    ((n++))
done
```
## 使用read命令读取变量数据  

```bash
while read paraa parab parac
do
    echo "PARAA:"$paraa  
    echo "PARAB:"$parab  
    echo "PARAC:"$parac  
done < datafile.txt
```

# 5. 其他



