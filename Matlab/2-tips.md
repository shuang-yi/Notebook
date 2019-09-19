# 心得

## 1. 画一个面，添加透明度

```
h = patch(x,y,z,C);
alpha(h,0.2); %设定透明度
```
`x,y,z`具有相同的大小`(m,n)`，总共`n`个面，每个面`m`个点，如果`C`是一个`1*n*3`的矩阵，则`n`个颜色对应`n`个面

## 2. 查找某个命令在哪些文件里调用过

```
grep -r --color='auto' --include '*.m' 'ipdiris' *
```
`-r` 递归目录
`--color='auto'` 匹配部分显示带颜色
`--include '*.m'` 只查找m文件
`'ipdiris'` 匹配字符串
`*` 所有文件

已经写好的程序：`where_used`

## 3. 保存matlab函数内变量

```
function funA
persistent X Y
...
end
```
在funA被多次调用时，始终保存X和Y。与全局变量类似，但是X和Y只能在funA中被调用。

## 4. 双纵轴

```matlab
yyaxis left;
plot(ser.tt,ser.y,'o-')
ylabel('Precipitation (mm)')
        
yyaxis right;
plot(ser.tt,ser.y,'o-')
ylabel('Temperature (^oC)');
```

## 5. 变量名为变量

变量名放在变量中。可以先用变量生成字符串再执行：`eval(string)`，或者结构体专用的：`struct.(svarname)`

## 6. 结构体赋值

b是(1:20)结构体，含有域.lon，把lon依次赋值为1到20
```matlab
a = num2cell(1:20);
[b.lon] = deal(a{:});
```

## 7. 统计出现次数

```matlab
A = round(rand(1,100)*100);
A2 = unique(A); % 剔除重复的数
n = histc(A,A2); % 统计各个数出现的次数
```
N = histc(X,EDGES)
N(k) will count the value X(i) if EDGES(k) <= X(i) < EDGES(k+1).

## 8. 拼接矩阵

```matlab
C = cat(dim, A, B)       %按dim来联结A和B两个数组。
cat(2, A, B) %相当于[A, B];
cat(1, A, B) %相当于[A; B].
```



# MATLAB代码体系

## 逻辑

所有函数的代码位于：`/Users/Yish/workplace/projects/#program/share/`

### 关键词keyword

- 函数文件中带有关键词，关键词格式为`{{xxx}}`，一个函数可以带多个关键词，如`%{{string}} {{find}}`
- 关键词可以用`search`命令查找。
- 所有的关键词可以用`all_keywords`查看

#### 划分文档结构

一个文档里的结构可以用关键词划分，用函数`disp_struct(filename)`可以打印出文档结构。需要在关键词前面指定显示的级别，如`% 1 {{keyword}}`，如果不指定级别，将是0级，每个级别对应两个空格的缩进

### 代码笔记snip

- 可以用`snip`函数查看代码笔记的标题
- 用`open snip_code`打开代码笔记，用`cmd+F`查找关键信息

## 重要命令

### search

查找关键词，默认在`share`路径下。

```matlab
search('list','data')
search('fun','LLZ_forward')
search('kw','acceleration') % {{keyword}}
search('kw',{'time','plot'}) % multiple keywords
search(..., 'path','share') % registered in 'ipdiris'
search(..., 'open', ilist) % open the ilist file/dir
search(..., 'open', -ilist) % open the ilist file/dir outside MATLAB
search(..., 'opendir', -ilist) % open the ilist dir outside MATLAB
```

### all_keywords

显示所有关键词，默认只显示`share`路径下

### ipdiris

重要路径的快速索引，输入关键词，返回完整路径

# 约定

## LLZ

LLZ.lon, LLZ.lat, LLZ.rg, LLZ.tt
short for lonlat, Z

## SH

SH(1).C, SH(1).S, SH(1).tt

## tt

tt=[SH.tt];

## 平均场

2003年1月到2010年12月

## 命名规则

o_开头表示可选的
s_开头表示结构数组

## 颜色

![-c](E:\git\Notebook\Matlab\media\Pasted Graphic 4.png)

```
[0,90,178;
208,61,3;
233,164,0;
106,20,125;
100,161,27;
59,175,236;
145,0,33]
```

![工作簿1 Microsoft Excel, 今天 at 下午8.10.32](E:\git\Notebook\Matlab\media\工作簿1 Microsoft Excel, 今天 at 下午8.10.32.png)

```
[75,135,203;
230,104,37;
148, 148, 148;
253, 181, 10;
53, 91, 183;
95, 161, 55]
```

### figure全屏

```
scrsz = get(groot,'ScreenSize');
figure('Position',[1 scrsz(4) scrsz(3) scrsz(4)])
```

## Log

### Rename

| Old                 | New                  |
| ------------------- | -------------------- |
| generate_SH         | SH_generate          |
| rg_write            | LLZ_write            |
| rg_cut              | LLZ_cut              |
| rg_extract          | LLZ_extract          |
| rg_create_enumerate | LLZ_create_enumerate |
| rg_info             | LLZ_info             |
| rg_180to360         | LLZ_180to360         |
| rg_1Dto2D           | LLZ_1Dto2D           |
| two_LLZ_compatible  | LLZ_two_compatible   |
| wrap_check          | LLZ_wrap_check       |



