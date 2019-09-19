# 小技巧
## 设置
### 临时设置
临时设置：`--PARAMETER=VALUE`，如`--FONT_TILE=12p`
## 坐标格式
### 设定画图经度+-180或0~360
	
```
gmt set FORMAT_GEO_MAP=+D
```

`FORMAT_GEO_MAP`有两种格式：` [+|-]D` or `[+|-]ddd[:mm[:ss]][.xxx][F]`


* +D Output longitude in the range [0,360]
* -D Output longitude in the range [-360,0]
* D Use FORMAT_FLOAT_OUT for floating point degrees.
* ddd Fixed format integer degrees
* : delimiter used
* mm Fixed format integer arc minutes
* ss Fixed format integer arc seconds
* .xxx Floating fraction of previous integer field, fixed width.
* F Encode sign using WESN suffix
* G Same as F but with a leading space before suffix
* The default is D.


### -X -Y
前缀a表示这次的偏移对下次无效。
前缀f表示相对纸张的绝对移动
前缀c表示相对纸张中心的移动
使用，但是不接参数，表示继承上一步参数

### 显示经纬度
	gmt set MAP_FRAME_AXES=WESnZ

## 其他
### 1.把ps扩展名改为png

```
${ps%ps}png #delete 'ps', add 'png'
```
## 转换格式

```
gmt psconvert -Tg -P -A10p
```

