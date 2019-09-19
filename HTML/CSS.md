css

# head中定义
在head中定义样式，在body中用class指定样式

```htm
<html>
<head>
<style type="text/css">
h1.intro {color:blue;}
p.important {color:#ff2a2b;}
</style>
</head>

<body>
<h1 class="intro">Header 1</h1>
<p>A paragraph.</p>
<p class="important">请注意这个重要的段落。:)</p>
</body>

</html>
```

# 外部style样式

```htm
<head>
<link rel="stylesheet" type="text/css" href="theme.css" />
</head>
```

# 在正文中定义样式style

```htm
<h1 style="color:blue; text-align:center">This is a header</h1>
<p style="color:red">This is a paragraph.</p>
```

