# 小技巧与心得
## 1. export env set
linux变量分shell变量（set）、用户变量（env），前者包含后者
export把shell变量导出为当前用户的变量，export变量可以传递给子shell，不能上传给父shell
## 2. 返回结果赋值给变量

```
result=`COMMAND`
```
## 3. 脚本头

```
#! /bin/bash
```

## 4. wget批量下载球函数

```bash
$ wget http://icgem.gfz-potsdam.de/ICGEM/shms/monthly/grgs/
$ cat index.html | awk -F \" '{print $6}' > fileList
$ wget -i fileList
```

解释：
第一行：得到index.html文件
第二行：把html按照双引号分割，其中第6个域是我们需要的文件路径，放到fileList中
第三行，从fileList中依次读取文件并下载

fileList的一行内容为这样的格式：

```
http://icgem.gfz-potsdam.de/ICGEM/shms/monthly/gfz-rl05/GSM-2_2012311-2012335_0025_EIGEN_G---_0005.gfc
```

## 5. bc计算器
计算器，支持`+`、`-`、`*`、`/`、`^`（指数）、`%`（取余），逻辑运算，循环、判断，常用三角、对数、指数函数，函数定义。

```bash
pi=$(echo "scale=3; 4*a(1)" | bc -l)
```
`scale=3` ：设定显示三位小数
`-l` : 表示调用数学库
`a()` : 表示atan()

## 6. 生成有序数列seq

``` bash
seq 3 1 # 生成逆序：3 2 1
seq -w 9 12 # -w生成补零：09 10 11 12
seq 0 0.05 0.1 # 生成带小数：0 0.05 0.10
seq -w 0 0.05 0.1 # 生成补零带小数：0.00 0.05 0.10
```



