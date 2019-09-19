[x] Matlab时间函数

# 存储方式
## 1. 数值
公元0年到某一天的天数，如`2008年8月26日12点`表示为`733646.5`
## 2. 字符串
定义了31种标准日期格式
例如：`dd-mmm-yyyy HH:MM:SS`，表示`01-Mar-2000 15:45:17`

简表1：

符号    |例子  | 符号 |例子  |符号   |例子
------|------|------|------|------|------
yyyy  |2000  |yy    |90, 00|m     | J, F, M
mmmm  |March |mmm   |Mar   |mm    |03
dddd  |Monday|ddd   |Mon   |dd    |01
d     |M,T   |HH    |22:20; 9:00 AM |MM | 10:15, 10:05 AM
SS    |10:05:30, 10:05:30 AM |FFF| 10:15:30.015 | PM | AM or PM 

更多参见下文的附录中的表1和表2。
 
## 3. 向量
6元素数组来表示日期和时间，如`[2008 8 26 12 5 0]`表示`2008年8月26日12点5分0秒`
3元素数组来表示日期。
## 4. 三种格式间的转换
- `datestr`：另外两种格式转为字符串
- `datenum`：另外两种格式转为数值
- `datevec`：另外两种格式转为向量

# 内建函数
## 1. 显示时间
- `clock`：当前日期时间放在向量格式中

```
>> format shortg
>> clock
ans =
2016  2  21  16  46  47.433
```

- `now`：当前日期时间，放在数值格式中

- `date`：当前日期，放在字符串格式中`dd-mmm-yyyy`

```
>> date
ans =
21-Feb-2016
```

- `tic | toc`：程序运行计时开始 | 结束

## 2. 查询时间信息
- `calender`：显示日历

```
>> calendar
                   Feb 2016
     S     M    Tu     W    Th     F     S
     0     1     2     3     4     5     6
     7     8     9    10    11    12    13
    14    15    16    17    18    19    20
    21    22    23    24    25    26    27
    28    29     0     0     0     0     0
     0     0     0     0     0     0     0
```
- `D = eomday(Y,M)`：一个月的天数

## 3. 时间转换
- `[DAYNUM,DAYNAME] = weekday(T)`：转换为周几（周日是第一天）

```
>> [num,name] = weekday('19-Dec-1994')
num =
     2
name =
Mon
```
## 4. 其他
- `datetick('x','yyyy-mm')`：时间坐标轴，画图用，这里把x轴变成`yyyy-mm`格式的时间

# 附录
## Table 1: Standard MATLAB Date format definitions
 
Number              |String                  |Example
------------------- |------------------------|-------------
       0            |'dd-mmm-yyyy HH:MM:SS'  |01-Mar-2000 15:45:17 
       1            |'dd-mmm-yyyy'           |01-Mar-2000  
       2            |'mm/dd/yy'              |03/01/00     
       3            |'mmm'                   |Mar          
       4            |'m'                     |M            
       5            |'mm'                    |03            
       6            |'mm/dd'                 |03/01        
       7            |'dd'                    |01            
       8            |'ddd'                   |Wed          
       9            |'d'                     |W            
      10            |'yyyy'                  |2000         
      11            |'yy'                    |00           
      12            |'mmmyy'                 |Mar00        
      13            |'HH:MM:SS'              |15:45:17     
      14            |'HH:MM:SS PM'           | 3:45:17 PM  
      15            |'HH:MM'                 |15:45        
      16            |'HH:MM PM'              | 3:45 PM     
      17            |'QQ-YY'                 |Q1-96        
      18            |'QQ'                    |Q1           
      19            |'dd/mm'                 |01/03        
      20            |'dd/mm/yy'              |01/03/00     
      21            |'mmm.dd,yyyy HH:MM:SS'  |Mar.01,2000 15:45:17 
      22            |'mmm.dd,yyyy'           |Mar.01,2000  
      23            |'mm/dd/yyyy'            |03/01/2000 
      24            |'dd/mm/yyyy'            |01/03/2000 
      25            |'yy/mm/dd'              |00/03/01 
      26            |'yyyy/mm/dd'            |2000/03/01 
      27            |'QQ-YYYY'               |Q1-1996        
      28            |'mmmyyyy'               |Mar2000        
      29 (ISO 8601) |'yyyy-mm-dd'            |2000-03-01
      30 (ISO 8601) |'yyyymmddTHHMMSS'       |20000301T154517 
      31            |'yyyy-mm-dd HH:MM:SS'   |2000-03-01 15:45:17 
 
## Table 2: Date format symbolic identifiers (Examples are in US English)
    
Symbol     |Interpretation of format symbol
-----------|-----------------------------
    yyyy   |full year, e.g. 1990, 2000, 2002
    yy     |partial year, e.g. 90, 00, 02
    mmmm   |full name of the month, according to the calendar locale, e.g. "March", "April". 
    mmm    |first three letters of the month, according to the calendar locale, e.g. "Mar", "Apr". 
    mm     |numeric month of year, padded with leading zeros, e.g. ../03/.. or ../12/.. 
    m      |capitalized first letter of the month, according to the calendar locale; for backwards compatibility. 
    dddd   |full name of the weekday, according to the calendar locale, e.g. "Monday", "Tuesday". 
    ddd    |first three letters of the weekday, according to the calendar locale, e.g. "Mon", "Tue". 
    dd     |numeric day of the month, padded with leading zeros, e.g.  05/../.. or 20/../.. 
    d      |capitalized first letter of the weekday; for backwards compatibility
    HH     |hour of the day, according to the time format. In case the time format `AM | PM` is set, HH does not pad with leading zeros. In case `AM | PM` is not set, display the hour of the day, padded with leading zeros. e.g 10:20 PM, which is equivalent to 22:20; 9:00 AM, which is equivalent to 09:00.
    MM     |minutes of the hour, padded with leading zeros, e.g. 10:15, 10:05, 10:05 AM.
    SS     |second of the minute, padded with leading zeros, e.g. 10:15:30, 10:05:30, 10:05:30 AM. 
    FFF    |milliseconds field, padded with leading zeros, e.g. 10:15:30.015.
    PM     |insert AM or PM in date string



