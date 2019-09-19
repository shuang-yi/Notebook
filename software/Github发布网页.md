# 在Github发布网页
## 准备工作
### 1. 注册GitHub账号
### 2. 创建SSH Key

参见[网络教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000)

## GitHub站点
个人站点（非organization）分两种格式，`User Pages` 和 `Project Pages`

### User Pages
* 用户站点格式必须为`username.github.io`
* `master`分枝的内容会用来建立站点
* 访问路径为`http(s)://<username>.github.io`

### Project Pages
放在一个仓库（repository）里
访问格式为`http(s)://<username>.github.io/<projectname>`
`gh-pages`分枝用来显示站点

## mweb发布到Github
[mweb官方帮助](http://zh.mweb.im/sync-webistes-to-github-or-ftp-zh.html)
核心代码：

```
git add .
git commit -m "first commit"
git remote add origin https://github.com/shuang-yi/shuang-yi.github.io.git
git push -u origin master
```
origin即为远程库的名称（这是Git默认的远程库叫法，也可以改成其他的）
`git push`表示把当前分支`master`推送到远程

由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

从现在起，只要本地作了提交，就可以通过命令：

```
$ git push origin master
```
把本地master分支的最新修改推送至GitHub
# Git入门
## 1. 创建版本库
在路径下输入

```
$ git init
Initialized empty Git repository in /Users/Yish/workplace/github/learngit/.git/
```
瞬间Git就建好了一个空的仓库（empty Git repository），并且当前目录下多了一个`.git`的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件。

## 2. 添加文件
在当前路径下创建一个`readme.txt`，里面内容为：

```
Git is a version control system.
Git is free software.
```

第一步，用命令`git add`告诉Git，把文件添加到仓库（将没有任何反馈）：

```
$ git add readme.txt
```

第二步，用命令`git commit`告诉Git，把文件提交到仓库：

```
$ git commit -m "wrote a readme file"
[master (root-commit) 6306056] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

`git commit`命令执行成功后会告诉你，1个文件被改动（我们新添加的readme.txt文件），插入了两行内容（readme.txt有两行内容）。

## 3. 简单参考

### 3.1. 基本

* `git init`：新建
* `git status`：查看改动信息（会显示是否添加到仓库）
* `git diff readme.txt`：查看readme.txt具体差异
* `git add readme.txt`：提交到仓库
* `git add .`添加所有修改，删除或新建的文件到缓存区
* `git commit -m "message`：提交修改，设定信息为message
* `git log`：显示从最近到最远的提交日志
* `git log --pretty=oneline`：简单显示提交日志

### 3.2 分支

* `git branch develop`：创建develop分支
* `git checkout develop`：切换到develop分支，checkout可以换为`switch`
* `git checkout -b develop`：创建并切换‘develop'新分支
* `git switch -c develop`：上面命令的另一个版本，减少歧义
* `git branch`：显示所有分支
* `git merge dev`：把dev合并到当前分支
* `git branch -d dev`：删除dev分支
* `git status`：查看哪些文件有冲突，再手动挨个修改（冲突已经同步进入了文档），最后再提交一次
* `git log --oneline --decorate --graph --all`：树状图查看分支情况

### 3.3 添加远端克隆

* `git remote add origin https://github.com/YOU/REPONAME.git`：这里命名为’origin‘
* `git pull origin master`：从远端‘origin’上的‘master’分支下载
* `git clone git@github.com:github/hub.git`：相当于`init, remote add, pull`三个命令的缩写
* `git push origin master`：保存到远端，remote名字为origin


