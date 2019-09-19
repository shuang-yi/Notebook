# 3. find
`man find` in MAC  OS

```
find / \! -name "*.c" -print
```
Print out a list of all the files whose names do not end in .c.


```
find / -newer ttt -user wnj -print
```
Print out a list of all the files owned by user ``wnj'' that are newer than the file ttt.


```
find / \! \( -newer ttt -user wnj \) -print
```
Print out a list of all the files which are not both newer than ttt and owned by ``wnj''.


```
find / \( -newer ttt -or -user wnj \) -print
```
Print out a list of all the files that are either owned by ``wnj'' or that are newer than ttt.


```
find / -newerct '1 minute ago' -print
```
Print out a list of all the files whose inode change time is more recent than the current time minus one minute.


```
find / -type f -exec echo {} \;
```
Use the echo(1) command to print out a list of all the files.


```
find -L /usr/ports/packages -type l -exec rm -- {} +
```
Delete all broken symbolic links in /usr/ports/packages.


```
find /usr/src -name CVS -prune -o -depth +6 -print
```
Find files and directories that are at least seven levels deep in the working directory /usr/src.


```
find /usr/src -name CVS -prune -o -mindepth 7 -print
```
Is not equivalent to the previous example, since -prune is not evaluated below level seven.




