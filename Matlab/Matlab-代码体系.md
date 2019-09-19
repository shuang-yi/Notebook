# MATLAB代码体系

## 逻辑
所有函数的代码位于：`/Users/Yish/workplace/projects/#program/share/`

### 关键词keyword

* 函数文件中带有关键词，关键词格式为`{{xxx}}`，一个函数可以带多个关键词，如`%{{string}} {{find}}`
* 关键词可以用`search`命令查找。
* 所有的关键词可以用`all_keywords`查看

#### 划分文档结构
一个文档里的结构可以用关键词划分，用函数`disp_struct(filename)`可以打印出文档结构。需要在关键词前面指定显示的级别，如`% 1 {{keyword}}`，如果不指定级别，将是0级，每个级别对应两个空格的缩进

### 代码笔记snip

* 可以用`snip`函数查看代码笔记的标题
* 用`open snip_code`打开代码笔记，用`cmd+F`查找关键信息

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


