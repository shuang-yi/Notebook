# 2. awk
与sed比较
awk常常以一行中的每个“子段”为单位来处理。
sed常常以“一行”为单位处理。

## 示例:

### 跳过header，输出指定列
跳过1个Header读取1.dat，输出1、2、5列到2.dat中

```bash
cat 1.dat | awk 'NR>1 { print $1, $2, $5 }' > 2.dat
```

### 算数求和输出
增加第三列，为前两列的和，格式化输出（printf为shell命令），分号隔开多个命令。

```bash
cat pay.txt |\
awk 'NR==1 {printf "%10s %10s %10s\n" ,$1,$2, "Total" } \
NR>=2{ total = $1 +$2; printf "%10d %10d %10.2f\n",$1,$2,total}' 
```

### 指定分隔符，条件判断 

```bash
cat /etc/passwd |\
awk 'BEGIN {FS=":"} $3 < 10 {print $1 "\t" $3}'
```
	
- file 按照正则表达式的值做为分隔符，这里代表空格、:、TAB、|同时做为分隔符。
  
```bash
awk -F '[ :\t|]' '{print $1}' 
```

### awk中调用系统变量

```bash
Flag=abcd
awk '{print '$Flag'}'    # 结果为abcd
```
### awk传递变量给shell

```bash
eval $(awk 'BEGIN{print "a=1"; print "b=2"}') # 经验证测试，a 是 1，b 是 2
```

## 语法

```bash
awk [option] '条件类型1{动作1};条件类型2{动作2};...' filename1 filename2 ...     
cat filename | awk …多个命令用 回车或者分号分开 
```
### 选项option
`-F fs` : 使用`fs`作为输入记录的字段分隔符，如果省略该选项，awk使用环境变量IFS的值
`-f filename` : 从文件`filename`中读取awk_script
`-v var=value` : 为awk_script设置变量，或者`awk '{print $0}' var=value`
### 变量名
`NR` ：当前处理“第几行”；
`NF` ：每一行拥有的字段总数；
`FS` ：目前分隔字符，默认空格与 tab。`{FS=":"}` ：指定冒号分隔符
`ARGC` ： 命令行变元个数
`ARGV` ： 命令行变元数组
`FILENAME` ： 当前输入文件名
`FNR` ： 当前文件中的记录号
`RS` ： 输入记录分隔符
`OFS` ： 输出域分隔符
`ORS` ： 输出记录分隔符
### 条件
省略表示对所有行均处理，有指定行号和条件判断两种方式：
#### 指定行号
`NR > 1`，跳过文件头
`BEGIN`,`END`，分别代表读入前，读入完后
`NR>=2&& NR<=5` ：混合表达式
#### 条件判断
比较：`> < <= >= == != `
匹配：`value ~ /regexp/`， 如果value匹配/regexp/，则返回真，例如，`$3 ~ /^d/`

支持混合表达式：`&&`与、`||`或、`!`非
例如：`($1< 10 ) && ($2 > 10)`，`/^d/||/x$/ `      

匹配也支持范围  `/start/,/end/`        
### 其他
1.	读入一条记录，对所有“条件+动作”处理完后再读入下一条
2.	字符串用双引号，因为awk自己使用了单引号

