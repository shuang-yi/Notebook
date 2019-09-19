# Matlab API

网址：http://gmt.soest.hawaii.edu/projects/gmt-matlab-octave-api/wiki

	addpath /opt/gmt/bin
	
## 设定系统路径
	pathlist = getenv('PATH');
	if isempty( strfind(pathlist,'/opt/local/bin') )
		setenv('PATH',['/opt/local/bin:/opt/local/sbin:/opt/gmt/bin/:/usr/local/bin/:/opt/X11/bin:', pathlist])
	end
## 还原
	setenv('PATH','/usr/bin:/bin:/usr/sbin:/sbin')

## 环境设定
由于matlab自带的动态链接库有问题，需要屏蔽这个变量才能使用`psconvert`命令
```
libpath='/Applications/MATLAB_R2016b.app/sys/os/maci64:/Applications/MATLAB_R2016b.app/bin/maci64/../../Contents/MacOS:/Applications/MATLAB_R2016b.app/bin/maci64:/Applications/MATLAB_R2016b.app/extern/lib/maci64:/Applications/MATLAB_R2016b.app/runtime/maci64:/Applications/MATLAB_R2016b.app/sys/java/jre/maci64/jre/lib/./native_threads:/Applications/MATLAB_R2016b.app/sys/java/jre/maci64/jre/lib/./server:/Applications/MATLAB_R2016b.app/sys/java/jre/maci64/jre/lib/./lib/jli'

libpath = getenv('DYLD_LIBRARY_PATH');
setenv('DYLD_LIBRARY_PATH','');

```	
## 测试：

	gmt
	gmt ('psbasemap', '-R0/10/0/15 -JM6i -P -Baf -BWSne+glightblue > map1.ps')
	gmt ('pscoast', '-R0/10/0/15 -JM6i -P -Baf -BWSne -Glightbrown > map2.ps')
	
	coast = gmt ('gshhg', 'gshhs_i.b --IO_SEGMENT_MARKER=N');

### 带cpt的参数	
	cpt = gmt('grd2cpt -Cblue,red', G);
	gmt('grdimage -JX8c -Ba -P -C -G > crap_img.ps', G, cpt)
两个输入，重要的在前面，`-C`，`-G`是两个空开关，为了更易读

### pstext输入参数
	lines = {'5 6 Some label', '6 7 Another label'};
	gmt('pstext -R0/10/0/10 -JM6i -Bafg -F+f18p -P > text.ps', lines)

# 程序
程序目录：/Users/Yish/workplace/projects/#program/share/program/GMT

##### gmt_dat2grd：插值

```
data = LLZ;
gset.dpi = 1;
gset.ran = 'g';
tmpgrd = gmt_dat2grd(data,gset)
```
data可以是三列数据或者LLZ
`tmpgrd.Z(Nlat*Nlon), tmpgrd.X(1*Nlon), tmpgrd.Y(1*Nlat)`

##### gmt_image：二维图
```matlab
gset = struct('ran','g',...
    'proj','Q85/40/18c',...
    'position','-X2 -Y3',...
    'xinfo','a60',...
    'yinfo','a30',...
    'binfo2','WSne+t"trend plot"',...
    'dpi', 1,...
    'cran', '-5/5/1',...
    'barinfo','1/:cm/yr:',...
    'width', 10,...
    'gap', 1.5, ...
    'MAP_FRAME_TYPE','fancy'); % plain/fancy

LLZ = load_LLZ('csr_trend_03-14_EWH_G300_PxMy');
opps = 'plot1-2.ps';
gmt_image(LLZ, opps, gset )
```

