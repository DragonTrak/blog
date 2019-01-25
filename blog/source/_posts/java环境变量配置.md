---
title: java环境变量配置
date: 2019-01-25 15:41:21
categories: "java"
tags:
	- java
---
### jdk安装
- 解压 tar -zxvf jdk-8u191-linux-x64.tar.gz

### 环境变量配置
- 修改/etc/profile 
- source /etc/profile 修改生效
- 创建软连接 方便版本更换和学习使用
```
ln -s jdk1.8.0_191 jdk
```
```
文件所有用户的shell都有权使用这些环境变量
vi /etc/profile
JAVA_HOME=/home/hadoop/app/jdk
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
PATH=$JAVA_HOME/bin:$PATH
export JAVA_HOME CLASSPATH PATH
```
- 修改.bashrc 文件
- 这些环境变量的权限控制到用户级别,这里是针对某一个
特定的用户，如果你需要给某个用户权限使用这些环境变量，你只需要修改其个人用户主目
录下的.bashrc 文件 
- source ~/.bashrc 修改生效
```
vi ~/.bashrc
JAVA_HOME=/home/hadoop/app/jdk
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
PATH=$JAVA_HOME/bin:$PATH
export JAVA_HOME CLASSPATH PATH
```