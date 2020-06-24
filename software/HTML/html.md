# 主体

```htm
<!DOCTYPE HTML>
<html>
<body>


</body>
</html>
```

# 标签
一些常用的标签使用示例

```htm
<!--这是一段注释。注释不会在浏览器中显示。-->
<a href="http://www.w3school.com.cn">链接</a>
<p>这是一段普通的段落。</p>
```



## id
利用id精准定位。采用JavaScript改变h1中的文字

```htm
<html>
<head>
<script type="text/javascript">
function change_header()
{
document.getElementById("myHeader").innerHTML="Nice day!";
}
</script>
</head>

<body>

<h1 id="myHeader">Hello World!</h1>
<button onclick="change_header()">Change text</button>

</body>
</html>
```

# CSS
继承样式
定义某一类
```htm
body {
  color: #000;
  background: #fff;
  margin: 0;
  padding: 0;
  font-family: Georgia, Palatino, serif;
  }

td, ul, ol, ul, li, dl, dt, dd  {
  font-family: Verdana, sans-serif;
  }

p {
  font-family: Times, "Times New Roman", serif;
  }
```
定义一个class

```
.classname {}
```
定义一个id

```
#idname {}
```
## 常见样式
背景：`p {background-color: gray; padding: 20px;}`
缩进：`p {text-indent: 5em;}`
行高：`p.small {line-height:90%} p.big {line-height:200%}`
水平对齐：`h1 {text-align:center} h2 {text-align:left} h3 {text-align:right}`
不要忽略换行和回车：`p {white-space: pre;}`
加粗：`p.thick {font-weight: bold}`
字体大小：`p {font-size:14px;}`
斜体：`p.normal {font-style:normal;} p.italic {font-style:italic;}`
字体：`p {font-family: Times, TimesNR, 'New Century Schoolbook', Georgia, 'New York', serif;}`

### 关于字体
- 多个字体供备选
- 含空格的名称需要引号引起来（单引号双引号皆可）
- 四大类：
	- serif（衬体）: Times、Georgia 和 New Century Schoolbook
	- sans-serif（非衬体）: Helvetica、Geneva、Verdana、Arial 或 Univers
	- Monospace（等宽）: Courier、Courier New 和 Andale Mono
	- Cursive（手写体）: Zapf Chancery、Author 和 Comic Sans


