#心得

# 1. 画一个面，添加透明度
```
h = patch(x,y,z,C);
alpha(h,0.2); %设定透明度
```
`x,y,z`具有相同的大小`(m,n)`，总共`n`个面，每个面`m`个点，如果`C`是一个`1*n*3`的矩阵，则`n`个颜色对应`n`个面

# 2. 查找某个命令在哪些文件里调用过
```
grep -r --color='auto' --include '*.m' 'ipdiris' *
```
`-r` 递归目录
`--color='auto'` 匹配部分显示带颜色
`--include '*.m'` 只查找m文件
`'ipdiris'` 匹配字符串
`*` 所有文件

已经写好的程序：`where_used`

# 3. 保存matlab函数内变量

```
function funA
persistent X Y
...
end
```
在funA被多次调用时，始终保存X和Y。与全局变量类似，但是X和Y只能在funA中被调用。

# 4. 双纵轴

```matlab
yyaxis left;
plot(ser.tt,ser.y,'o-')
ylabel('Precipitation (mm)')
        
yyaxis right;
plot(ser.tt,ser.y,'o-')
ylabel('Temperature (^oC)');
```

# 5. 变量名为变量
变量名放在变量中。可以先用变量生成字符串再执行：`eval(string)`，或者结构体专用的：`struct.(svarname)`

# 6. 结构体赋值
b是(1:20)结构体，含有域.lon，把lon依次赋值为1到20
```matlab
a = num2cell(1:20);
[b.lon] = deal(a{:});
```

# 统计出现次数

```matlab
A = round(rand(1,100)*100);
A2 = unique(A); % 剔除重复的数
n = histc(A,A2); % 统计各个数出现的次数
```
N = histc(X,EDGES)
N(k) will count the value X(i) if EDGES(k) <= X(i) < EDGES(k+1).

# 拼接矩阵

```matlab
C = cat(dim, A, B)       %按dim来联结A和B两个数组。
cat(2, A, B) %相当于[A, B];
cat(1, A, B) %相当于[A; B].
```