# 逻辑

## select
    switch method
    case {'aaa'}
      
    otherwise
    
    end



# New function

# 函数调用

## evalin

`evalin(WS,'expression')` 

和`eval`类似，但是可指定工作空间，WS can be 'caller' or 'base'. 

## assignin

`assignin(WS,'name',V)`

指定在工作空间WS赋值



# Matlab文件操作

##### filesep：目录分隔符

用于返回当前平台的目录分隔符，Windows是反斜杠(\)，Linux是斜杠(/)。

##### fullfile：字符串连成路径

用于将若干字符串连接成一个完整的路径。例如：

> > f=fullfile('D:','Matlab','example.txt')
> > f=D:\Matlab\example.txt
> > (在Windows中，“D:\”表示D盘，“D:”表示目录)

##### fileparts：文件名分割成4部分

用于将一个完整的文件名分割成4部分：路径，文件名，扩展名，版本号。例如：

> > f=fullfile('D:','Matlab','example.txt');
> > [pathstr,name,ext,versn]=fileparts(f)
> > pathstr=D:\Matlab
> > name=example
> > ext=.txt
> > versn=’’

##### pathsep：路径分隔符

返回当前平台的路径分隔符。Windows是分号(;)，Linux是冒号(:)。

##### exist：目录或者文件是否存在

可以用于判断目录或者文件是否存在，同时不同的返回值有不同的含义。例如：

> > f=fullfile('D:','Matlab','example.txt');
> > exist(f)
> > ans=2
> > exist('D:\Matlab')
> > ans =7

##### which：得到函数完整路径

可以通过一个函数或脚本名称得到它的完整路径,同时还能处理函数重载的情况，例如：

> > which abs(0)
> > C:\MATLAB7\toolbox\matlab\elfun\@double\abs.bi  % double method
> > which abs(single(0))
> > C:\MATLAB7\toolbox\matlab\elfun\@single\abs.bi  % single method

##### isdir：判断是否为路径

判断一个路径是否代表了一个目录，例如：

> > p='D:\Matlab';
> > f=fullfile(p,'example.txt');
> > isp=isdir(p)
> > isp=1
> > isf=isdir(f)
> > isf=0

##### dir：列出一个目录的内容

用于列出一个目录的内容，返回值为结构体数组类型，包含如下部分：name:文件或目录的名称；date:修改日期；bytes:文件大小；isdir:是否是目录。例如：

> > p='D:\Matlab';
> > files=dir(p)
> > files = 
> > 8x1 struct array with fields:
> >     name
> >     date
> >     bytes
> >     isdir

##### cd：切换当前工作目录

用于切换当前工作目录。例如：

> > cd('c:/toolbox/matlab/demos')        %切换当前工作目录到demos
> > cd ..        %切换当前工作目录到matlab

##### pwd：当前工作目录

用于当前工作目录的路径。例如：

> > pwd
> > ans =C:\MATLAB7\work

##### path：查询或添加搜索路径

用于对搜索路径的操作。例如：
<<path        %查询当前所有的搜索路径（MATLABPATH）
<<p=path                %把当前的搜索路径存在字符串变量p中
<<path(‘newpath’)                %将当前搜索路径设置为newpath
<<path(path,’newpath’)        %向路径添加一个新目录newpath
<<path(’newpath’, path)        %向当前搜索路径预加一个新目录nespath

##### addpath和rmpath：添加和删除搜索路径

用于对matlab搜索路径的添加和删除。例如：
<<addpath(‘directory’)        %将完整路径directory加入到当前搜索路径的最顶端
<<rmpath

##### what：显示目录下所有.m文件

用于显示出某目录下存在哪些matlab文件；若输入完整路径，可列出指定目录下的文件。例如：
<<what
<<what dirname
<<what(‘dirname’)
其中dirname是要查找的路径的名字，路径在matlab的搜索路径内时，没有必要输入全名，只输入最后或最后两级就够了。

##### path2rc：保存搜索路径到文件

保存当前matlab的搜索路径到pathdef.m文件中。



# 画图

## colormap

hsv
hot	黑-->红-->黄-->白
cool
pink
gray
bone
jet
copper
prim
flag

## 保存图片

`print('-dpng','-r150','filename.png')`

## 属性设置set @set

`get(gca)`：显示所有参数

## text函数

```
'Color','r'
'FontSize', 16
'FontWeight', 'bold'
'Rotation',文字旋转
'BackgroundColor'
```

## 线条与符号属性

```
color
LineWidth
MarkerEdgeColor
MarkerFaceColor
MarkerSize
edgecolor	网格，消除网格：set(h,'edgecolor','none')
```

## 边框

- `LineStyle`， 边框线型
- `LineWidth`，边框线条大小
- `Margin`，边框与文字间距

## 坐标轴

- 轴加上说明
  - `hh= xlabel(string) %ylabel,zlabel`
- 图例： `legend('string1','string2',…)`
- 设定刻度（其他的隐藏，会影响grid on）
  - `set(gca, 'ytick', [-1 -0.3 0.1 1]);`
  - `set(gca, 'ytick', []);`	%刻度清除
- 刻度替换
  - `set(gca,'xtick',[12 17 22 25],'xticklabel',{'11月2日';'11月7日';'11月12日';'11月15日'}) `
- 坐标轴加上文字
  - `hh= xlabel(string)`
- 刻度长度，小刻度
  - `set(gca,'xminortick','on');%style 5`
  - `set(gca,'ticklength',[0.05 0.025]);%style 6`
  - `set(gca,'tickdir','out');%style 7`
- 放置字符
  - `gtext('sin(x)');gtext('cos(x)') ; %鼠标放置，仅二维`
  - `text(pi/4, sin(pi/4),'\leftarrow sin(\pi/4) = 0.707');`
- 限定坐标范围
  - `axis([xmin,xmax…])` %-inf,inf为自动范围
  - `axis auto`
  - `axis equal`：横、纵轴等长刻度
  - `axis square`：产生正方形坐标系
  - `axis tight`：剪裁掉无图区域
- 网格
  - `grid on/off`
  - `set(gca,'xgrid','on')`
- 方框
  `box on/off`
- 设定colorbar范围
  `caxis([0,60]);`

## 窗口

### 新建窗口

`figure(h)`

### 分割窗口

`subplot (m, n, p)`
p 的算法为按行由左至右
直接使用：
`subplot('position',[left bottom width height])`

### 改变窗口背景颜色

指令                		說明
colordef white 圖軸背景為白色，視窗背景為淺灰色
colordef black 圖軸背景為黑色，視窗背景為暗灰色
colordef none 圖軸背景為黑色，視窗背景為黑色
     

### 改变视角

view(a,b)
view([x,y,z])
a是方位角，b是仰角

### 着色

`shading faceted`
系统默认，每个网格片用对应颜色（单色），保留网格线
`shading flat`
网格线也用相应颜色
`shading interp`
每个网格片插值着色，最光滑
     

### 光照

`light('Color',PAR,'Style',PAR,'Position',PAR)`

### 窗口重叠

```matlab
% axes('position',[left bottom width height])
h1 = axes('position',[0.1,0.1,0.8,0.8]);
ezplot('sin(x)');

h2 = axes('position',[0.5,0.5,0.3,0.3]);
ezplot('cos(x)');
```

subplot会强制删除重叠的坐标轴，axes不会

#### 设定下一个画图的坐标

```matlab
fig = gcf;
set(fig,'CurrentAxes',h2)
```

