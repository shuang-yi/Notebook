# meta与quota - shell十三问
## meta列表
简单而言，command line 的每一个 charactor ，分为如下两种：

* literal：也就是普通纯文字，对 shell 来说没特殊功能。
* meta：对 shell 来说，具有特定功能的特殊保留字符。
	* IFS：由 `<space>` 或 `<tab>` 或 `<enter>` 三者之一组成(我们常用 space )。是用来拆解 command line 的每一个词(word)用的，因为 shell command line 是按词来处理的。
	* CR：由 `<enter>` 产生，用来结束 command line 用的，这也是为何我们敲 <enter> 命令就会跑的原因。
	* `=`：设定变量。
	* `$`：作变量或运算替换(请不要与 shell prompt 搞混了)。
	* `>`：重导向 stdout。
	* `<`：重导向 stdin。
	* `|`：命令管线。
	* `&`：重导向 file descriptor ，或将命令置于背境执行。
	* `( )`：将其内的命令置于 nested subshell 执行，或用于运算或命令替换。
	* `{ }`：将其内的命令置于 non-named function 中执行，或用在变量替换的界定范围。
	* `;`：在前一个命令结束时，而忽略其返回值，继续执行下一个命令。
	* `&&`：在前一个命令结束时，若返回值为 true，继续执行下一个命令。
	* `||`：在前一个命令结束时，若返回值为 false，继续执行下一个命令。
	* `!`：执行 history 列表中的命令
 
(注一：关于 bash shell 在处理 command line 时的顺序说明，请参考 O'Reilly 出版社之 Learning the Bash Shell, 2nd Edition，第 177 - 180 页的说明，尤其是 178 页的流程图 Figure 7-1 ... )
 

## 关闭meta
 
假如我们需要在 command line 中将这些保留字符的功能关闭的话，就需要 quoting 处理了。
在 bash 中，常用的 quoting 有如下三种方法：

* hard quote：`' '` (单引号)，凡在 hard quote 中的所有 meta 均被关闭。
* soft quote： `" "` (双引号)，在 soft quoe 中大部份 meta 都会被关闭，但某些则保留(如 `$` )。(注二)
* escape ： `\` (反斜线)，只有紧接在 escape (跳脱字符)之后的单一 meta 才被关闭。
 
下面的例子将有助于我们对 quoting 的了解：

```
$ A=B C        # 空格键未被关掉，作为 IFS 处理。
$ C: command not found.
$ echo $A
       
$ A="B C"        # 空格键已被关掉，仅作为空格键处理。
$ echo $A
B C
```
在第一次设定 A 变量时，由于空格键没被关闭，command line 将被解读为：`A=B` 然后碰到<IFS>，再执行 C 命令
在第二次设定  A 变量时，由于空格键被置于 soft quote 中，因此被关闭，不再作为 IFS ：`A=B<space>C`
事实上，空格键无论在 soft quote 还是在 hard quote 中，均会被关闭。

### 不同quote对回车的不同解读
#### hard quote
```
$ A='B
> C
> '
$ echo "$A"
B
C
```
在上例中，由于 `<enter>` 被置于 hard quote 当中，因此不再作为 CR 字符来处理。
这里的 `<enter>` 单纯只是一个断行符号(new-line)而已，由于 command line 并没得到 CR 字符，因此进入第二个 shell prompt (PS2，以 `>` 符号表示)，command line 并不会结束，直到第三行，我们输入的 `<enter>` 并不在  hard quote 里面，因此并没被关闭，此时，command line 碰到 CR 字符，于是结束、交给 shell 来处理。

#### soft quote
上例的 `<enter>` 要是被置于 soft quote 中的话， CR 也会同样被关闭：

```
$ A="B
> C
> "
$ echo $A
B C
```
 
然而，由于 `echo $A` 时的变量没置于 soft quote 中，因此当变量替换完成后并作命令行重组时，`<enter>` 会**被解释为 IFS** ，而不是解释为 New Line 字符。

#### escape
同样的，用 escape 亦可关闭 CR 字符：

```
$ A=B\
> C\
>
$ echo $A
BC
```
 
上例中，第一个 `<enter>` 跟第二个 `<enter>` 均被 escape 字符关闭了，因此也不作为 CR 来处理，但第三个 `<enter>` 由于没被跳脱，因此作为 CR 结束 command line 。但由于 `<enter>` 键本身在 shell meta 中的特殊性，在 `\` 跳脱后面，**仅仅取消其 CR 功能，而不会保留其 IFS 功能**。
 
您或许发现光是一个 <enter> 键所产生的字符就有可能是如下这些可能：

* CR
* IFS
* NL(New Line)
* FF(Form Feed)
* NULL

至于甚么时候会解释为甚么字符，这个我就没去深挖了，或是留给读者诸君自行慢慢摸索了... ^_^

### 不同quote对`$`的解读
至于 soft quote 跟 hard quote 的不同，主要是对于某些 meta 的关闭与否，以 $ 来作说明：

```
$ A=B\ C
$ echo "$A"
B C
$ echo '$A'
$A
```
在第一个 echo 命令行中，`$` 被置于 soft quote 中，将不被关闭，因此继续处理变量替换，因此 echo 将 A 的变量值输出到荧幕，也就得到  "B C" 的结果。在第二个 echo 命令行中，`$` 被置于 hard quote 中，则被关闭，因此 `$` 只是一个 `$` 符号，并不会用来作变量替换处理，因此结果是 `$` 符号后面接一个 A 字母：`$A` 。
 
练习与思考：如下结果为何不同？

```
$ A=B\ C
$ echo '"$A"'        # 最外面的是单引号
"$A"
$ echo "'$A'"        # 最外面的是双引号
'B C'
```
 (提示：单引号及双引号，在 quoting 中均被关闭了。)

## awk命令与shell关键字的冲突
在 CU 的 shell 版里，我发现有很多初学者的问题，都与 quoting 理解的有关。
比方说，若我们在 awk 或 sed 的命令参数中调用之前设定的一些变量时，常会问及为何不能的问题。
要解决这些问题，关键点就是：
**区分出 shell meta 与 command meta**

前面我们提到的那些 meta ，都是在 command line 中有特殊用途的，比方说 `{ }` 是将其内一系列 command line 置于不具名的函式中执行(可简单视为 command block )，但是，awk 却需要用 `{ }` 来区分出 awk 的命令区段(BEGIN, MAIN, END)。
若你在 command line 中如此输入：

```
$ awk {print $0} 1.txt
```
由于  { } 在 shell 中并没关闭，那 shell 就将 {print $0} 视为 command block ，
但同时又没有" ; "符号作命令区隔，因此就出现 awk 的语法错误结果。
要解决之，可用 hard quote ：

```
$ awk '{print $0}' 1.txt
```
上面的 hard quote 应好理解，就是将原本的 `{`、`<space>`、`$`(注三)、} 这几个 shell meta 关闭，避免掉在 shell 中遭到处理，而完整的成为 awk 参数中的 command meta 。
( 注三：而其中的 `$0` 是 awk 内建的 field number ，而非  awk 的变量，awk 自身的变量无需使用 `$` 。)
要是理解了 hard quote 的功能，再来理解 soft quote 与 escape 就不难：

```
awk "{print \$0}" 1.txt
awk \{print\ \$0\} 1.txt
```
## 变量名为变量
然而，若你要改变 awk 的 `$0` 的 0 值是从另一个 shell 变量读进呢？
比方说：已有变量 `$A` 的值是 0 ，那如何在 command line 中解决 awk 的 `$$A` 呢？
你可以很直接否定掉 hard quoe 的方案：

```
$ awk '{print $$A}' 1.txt
```
那是因为 `$A` 的 `$` 在 hard quote 中是不能替换变量的。
聪明的读者(如你!)，经过本章学习，我想，应该可以解释为何我们可以使用如下操作了吧：

```
A=0
awk "{print \$$A}" 1.txt
awk \{print\ \$$A\} 1.txt
awk '{print $'$A'}' 1.txt
awk '{print $'"$A"'}' 1.txt     # 注："$A" 包在 soft quote 中
```
或许，你能举出更多的方案呢....

