# GMT自带命令解析

## pstext

```bash
gmt pstext -F+jBL -Jx1c -R0/100/0/100 -Gred -K -O -N >> $ps << EOF
0.8 11.1 @:14:(a) Trend of GWS
17 11.3  @:12:(b) Trend of TTWS
17 5.5 @:12:(c) Trend of SWS
EOF
```
-G	填充色
-F[+a[angle]][+c[justify]][+f[font]][+h][+j[justify]][+l]
默认情况下，文字水平，字体属性来自FONT_ANNOT_PRIMARY，并且以经纬度为中心。开关后面不接属性，将从文件中读入相应属性。
+f to set the font (size,fontname,color)：
+h 字符内容为最近的 segment header 
+l 字符内容为最近的segment label
+c  从-R范围得到经纬度，如-F+cTL，得到画图范围左上角经纬度。
`+j [T|M|B][L|C|R]` 甜面包两侧肉

例如：
`-F+f12p,Helvetica-Bold,red+j+a`，字体已经设置好，另外两个从文件中读入。文件每列依次表示为：经度，纬度，对其，角度，字符内容

-W 文字周围矩形框
-C 矩形框放大尺寸，如15%，2p
-D	偏移
-N	超出边界不剪裁

字符内容支持直接设定：
@~			切换symbol字体
@%no%		设定字号，@%%取消
@-			切换下标
@+			切换上标
@#			切换小型大写字母
@;color;		字体颜色，@;;取消
@:size:		字体大小，@::取消
@_			下划线

## psxy

```
gmt psxy tmp-1.txt -R -J -Ss0.15c -W0.1p,gray@50 -O -K -Y-10c >> $ps
```
## psvelo

```bash
gmt psvelo $input -R -J -W1,blue -Se0.06/0.95/0 -A7p+a30+p0.5p,blue+e+gblue -Gblue -O -K >> $ps
```

输入文件格式：
经度，纬度，东西分量，南北分量，东西分量标准差，南北分量标准差，两方向协方差，站名（可选）
X, Y, Vx, Vy, Sigx, Sigy, Corxy, name

`-Se0.06/0.95/0`
e表示画速度椭圆，速度矢量长度缩放0.06倍，95%的误差椭圆，站名字符大小为0
线条由-W指定，填充由-G指定。

### 画垂直方向误差：

先把误差绝对值加到或减去速率，画直线（箭头大小为0）：

`-A0p+a30+p0.5p,gray`

再叠加速率

`-A7p+a30+p0.5p,red+e+gred`

## psxy画箭头

`echo 5 5 10 2|gmt psxy -JX10c -R0/10/0/10 -Ba2 -W1p,red -SV10p+e -V > 3.ps`

+e在尾部加箭头

V: 起点经度/纬度/转角/长度

## grdtrack
gmt grdtrack ridge.txt -Gspac.nc -C400k/2k/10k+v -Sm+sstack.txt > table.txt

## grdcontour
`gmt grdcontour $grd -C0.5 -A1+g220 -Gn1 -R -J -K -O >> $ps`
-C 等高线间隔
-A 标注数值间隔，+g标注文字背景色
-G 标注距离，n1，每个等高线标注一次。

## 指北箭头和比例尺

```
gmt pscoast  ... -Tf92/42.1/1.5/2 -Lf92/39.9/40/200k+lkm --FONT_LABEL=11p ... >> $ps
```

T[f|m]lon/lat/size/info
	[f/m]画图样式
		f: fancy mode
		m: magnetic rose
	lon/lat/size
		中心经纬度和大小
	info
		1：东西南北四个方向
		2：8个方向
		3：16个方向
		
L[f]lon/lat/slat/length+l*label*
	f画图样式
		fancy
	lon/lat
		画图的中心经纬度
	slat
		比例尺采用纬度
	length
		比例尺长度
	+l*label*
		label,单位


## makecpt

```
gmt makecpt -T$cran -Cpolar -G0/NaN -D -Z > $cptfile1
```

-G 截断cpt文件，NaN表示默认。
-D: outliner
-Z: continue
-I: 反转颜色顺序

```bash
 if [ ${#cran} -gt 4 ]; then
	gmt makecpt -T$cran -Cjet -Z -D> $cptfile
  else
	gmt grd2cpt $grd -T= -Cjet -Z > $cptfile
	#-T: - for R =|zmin|, + for R = |zmax|, _ for R = min(|zmin|, |zmax|), or = for R = max(|zmin|, |zmax|)
  fi
```


## psscale
```
# plot
gmt psscale -C$cptfile -B$barinfo -Dx0/$y_shift+w$width/0.5+e+h  -O -K >> $ps
```
注意这里-Dx表示图纸坐标，参考点变为左下角，+w后面是尺寸，+e是超范围的箭头指示

```bash
# colorbar
  if [ $ibar -eq 1 ]; then # horizontal bar
	# D : gap/2, down, width, height
	x_shift=$( echo "scale=3;0"|bc )
	y_shift=$( echo "scale=3;-$gap*0.8"|bc )
	gmt psscale -C$cptfile -B$cinfo -Dx$x_shift/$y_shift+w$width/0.5c+e+h  -O -K >> $ps
  elif [ $ibar -eq 2 ]; then # vertical bar
	# D : gap/2, down, width, height
	x_shift=$( echo "scale=3;$width+$gap/2"|bc )
	y_shift=$( echo "scale=3;0"|bc )
	gmt psscale -C$cptfile -B$cinfo -Dx$x_shift/$y_shift+w$width/0.5c  -O -K >> $ps
  fi
```

## basemap
### -B
`-B[axes][+b][+gfill][+n][+olon/lat][+ttitle]`
`-B[p|s][x|y|z][+l|Llabel][+pprefix][+uunit]`

`-B+t"$title" -Bxa5f1+l"Difference" -Bya0.2f0.1+l"Probability" `

## gmtset
### FORMAT_GEO_OUT

## pslegend

```
gmt pslegend -R -J -Dx2.7c/3c+w3.2c+jBL+l1.2 -F+p0.5p,black -K -O >>$ps <<EOF
N 1
S 3p s 3p white 1p,$color1 0.3c M1: no correct
S 3p s 3p white 1p,$color2 0.3c M2: uniform correct
S 3p s 3p white 1p,$color3 0.3c M3: non-uniform cor.
S 1p r 6p,1p white 1p,255/128/129 0.3c ocean mass
S 1p r 6p,0.5p white 0.25p,black 0.3c smoothed GSM
EOF
```

http://gmt.soest.hawaii.edu/doc/5.3.2/pslegend.html

-X -Y

-X[a|c|f|r]

a画图后还原偏移

c画图居中(也可以加偏移)

f参考点相对于图纸左下角的偏移

r[默认]偏移画图参考点