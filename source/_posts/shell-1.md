---
title: shell-1
date: 2018-11-20 16:56:11
tags:
- shell
- linux
---

## 前言

shell: 命令解释器  -> os

shell脚本贯穿于linux服务

弱类型语言：直接赋值，不用预定义类型，语法宽松

### 一、建立一个shell

##### 首行：#!/bin/bash 指定命令解释器（sh，bash，awk，tcl，python....)

#! 非第一行 则为注释， shell用#为注释

sh ，bash：sh 为bash 的软链接

#### 注：linux 默认bash， 首行可以不写语言标识语句

./xx.sh 执行 == bash xx.sh 执行

### 二、shell脚本的执行

shell 非交互运行：

1. 查找环境变量：**全局etc/profile.d/**         **bashrc** 

2. 非可执行权限：bash xx.sh

3. 可执行权限： ./ （chmod 755）

4. source 或 . 执行：类似include， 即将xx.sh加载到父脚本下使用，父脚本可使用xx.sh 的变量和返回值 


控制台窗口是一个shell，运行的脚本也是一个shell

用source 或.  加载，可以把脚本里的变量 共享给 控制台窗口shell！！

##### 注：想在一个脚本里调用另一个脚本里的函数和变量 要用 source或. 来include 其他脚本！！

$user: 用户名

##### 注：

##### n = 3

##### 单引号‘$n' 输出

##### 即为字符串$n

##### 双引号“$n”输出

##### 即为数字3

##### 反引号``是命令替换，命令替换是指Shell可以先执行反引号内的命令，将输出结果暂时保存，在适当的地方输出
```bash
cat > 1.sh
> bin=`dirname "$0"`

bash 1.sh
echo $bin   =====>\ (输出为\)
# 此时的bin为全局变量，不是1.sh中那个被赋值的局部变量
. 1.sh
echo $bin   =====>.（输出为.）
# 此时1.sh的内容已经被加载到当前控制台下执行，bin变量被共享
# $0是bash的文件名，在bash中一般使用cd `dirname $0`进入该脚本所在的目录中
```



### 三、shell规范

1. #!/bin/bash

2. \# Date: 2018-11-20

3. \# Author:

4. \# Email:

5. \# Functions:

6. \# Version:

##### 注：./vimrc 可配置 制动生成头部信息

### 四、变量

常用全局变量：$USER \$UID \$HOME \$SHELL \$PS1\$PWD

env, set .... 都可以看到很多



export 设置环境变量

**export PATH=/app/bin:$PATH**

常放于 /etc/profile

**unset 取消 环境变量 注销前临时生效，除非写到文件里！**











