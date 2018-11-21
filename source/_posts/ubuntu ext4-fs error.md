---
title: ETX4-fs error（已解决）
date: 2018-11-21 01:51:09
tags: unix OS fs-error
---

### 前言

再将ubuntu系统装到另一块完整的硬盘上时，由于某些原因，在重新开机以后会报大量的windows系统盘（sda1）ETX4-error，导致开机检测无法通过

由此可能会导致以下开机时bug：

先是：

ibus 报 fatal 

在一堆failed之后

出现大量的

ETX4-fs error

结果：无法开机，system login failed



### 一、解决方法

考虑到ahci会检测全部硬盘文件系统，ide只会检测当前启动分区

将硬盘从AHCI摸式切换至IDE/compatible, 重启即可！

验证成功，可以成功开机。



但此方法又有一点不足之处：切换了硬盘模式以后，导致windows 无法正确开机。



所以问题的根源还是出在windows上。

具体细节无法查明，但考虑到windows是在休眠状态挂起中，或者是在快速启动关机挂起中，很有可能因异常关机导致文件系统异常。



其二、windows之前有一次更新，更新后未经过 ”***正常完全的关机***“ 步骤，也可能导致文件系统异常

### 二、结论

所以，下次遇到该问题，可以考虑如下步骤解决

1. 正常启动windows，并正常且彻底的关机
2. 尝试启动ubuntu系统
3. 如未成功，尝试修改硬盘模式为IDE/compatible

