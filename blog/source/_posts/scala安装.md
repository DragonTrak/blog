---
title: scala安装
date: 2019-01-25 15:21:39
comments: true #是否可评论
toc: true
categories: "scala"
tags:	#标签
	- scala
	- 大数据
---

### scala安装
 - 解压  
 `tar -zxvf scala-2.11.8.tgz `
 - 建立链接  
 `ln -s scala-2.11.8 scala`
### 环境变量配置
- 修改.bashrc 文件  
这些环境变量的权限控制到用户级别,这里是针对某一个 特定的用户，如果你需要给某个用户权限使用这些环境变量，你只需要修改其个人用户主目 录下的.bashrc 文件
```
source ~/.bashrc 修改生效
vi ~/.bashrc
SCALA_HOME=/home/hadoop/app/scala
PATH=SCALA_HOME/bin:$PATH
export SCALA_HOME
```
- 查看scala版本  
`scala -version`