---
title: shell比较操作
date: 2020-01-09 22:22:08
tags: shell
categories: linux
---
# test命令判断
常用命令如下表：
<!--more-->
## 关于文件类型的判断
测试标志|代表意义|示例
--|:--|:--
-e	|判断文件是否存在|判断文件是否存在</p>test -e filename
-f	|该文件是否存在且为普通文件(file)|判断是否为普通文件</p>test -f filename && filetype="regulare file"
-d	|该文件是否存在且为目录(directory)|判断是否为目录</p>test -f filename && filetype="directory"

## 关于数值的判断
测试标志|代表意义|示例
--|:--|:--
-eq| 两数值相等 (equal)|test n1 -eq n2
-ne| 两数值不等 (not equal)|test n1 -ne n2
-gt| n1 大于 n2 (greater than)|test n1 -gt n2
-lt| n1 小于 n2 (less than)|test n1 -lt n2
-ge| n1 大于等于 n2 (greater than or equal)|test n1 -ge n2
-le| n1 小于等于 n2 (less than or equal)|test n1 -le n2

## 关于字符串的判断
测试标志|代表意义|示例
--|:--|:--
-z |判断字符串是否为空|test -z string 若 string 为空字串，则为 true
-n |判断字符串是否为非空|test -n string 若 string 为空字串，则为 false。注： -n 亦可省略
== |判断字符串是否相等|test str1 == str2	若相等，则返回 true
!= |判断字符串是否不等|test str1 != str2 若相等，则返回 false

# [ ... ] 判断符号
除了利用test命令进行测试，还可以利用中括号[...]来进行判断。
如下两个操作具有相同的效果
```
 # 判断HOME变量是否为空字符串
 test -z "${HOME}" #方式一

 [ -z "${HOME}" ]  #方式二

```

使用中括号[...]时需要注意：
- 在中括号內的每个元件都需要有空白键来分隔；
- 在中括号內的变量，最好都以双引号括起来；
- 在中括号內的常量，最好都以单或双引号括起来。

```
[ "$HOME" == "$MAIL" ]
[□"$HOME"□==□"$MAIL"□]
 ↑       ↑  ↑       ↑
```
参考文献：
http://linux.vbird.org/linux_basic/0340bashshell-scripts.php
