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

![-c](media/14804776109666/Pasted%20Graphic%204.png)

	[0,90,178;
	208,61,3;
	233,164,0;
	106,20,125;
	100,161,27;
	59,175,236;
	145,0,33]
	
![工作簿1 Microsoft Excel, 今天 at 下午8.10.32](media/14804776109666/%E5%B7%A5%E4%BD%9C%E7%B0%BF1%20Microsoft%20Excel,%20%E4%BB%8A%E5%A4%A9%20at%20%E4%B8%8B%E5%8D%888.10.32.png)

	[75,135,203;
	230,104,37;
	148, 148, 148;
	253, 181, 10;
	53, 91, 183;
	95, 161, 55]
	
### figure全屏
	scrsz = get(groot,'ScreenSize');
	figure('Position',[1 scrsz(4) scrsz(3) scrsz(4)])

## Log
### Rename

| Old |New  |
| --- | --- |
|  generate_SH|  SH_generate|
| rg_write | LLZ_write |
| rg_cut | LLZ_cut |
| rg_extract | LLZ_extract |
| rg_create_enumerate | LLZ_create_enumerate |
| rg_info | LLZ_info |
| rg_180to360 | LLZ_180to360 |
| rg_1Dto2D | LLZ_1Dto2D |
| two_LLZ_compatible | LLZ_two_compatible |
| wrap_check | LLZ_wrap_check |



