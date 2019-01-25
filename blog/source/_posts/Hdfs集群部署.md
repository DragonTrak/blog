---
title: Hdfs集群部署
date: 2019-01-25 17:43:38
categories: "hadoop"
tags:
	- hadoop
	- 大数据
---
### 安装hdfs
1.下载 Hadoop 安装包
```
Apache 版本下载地址： https://archive.apache.org/dist/hadoop/common/
CDH 版本下载地址： http://archive-primary.cloudera.com/cdh5/cdh/5/
下 载 对 应 版 本 Hadoop ， 这 里 下 载 hadoop-2.6.0-cdh5.10.0.tar.gz 版 本 ， 并 上 传 至
/home/hadoop/app 目录下。
```
2.修改配置

3.分发
	将配置分发到各节点  
4.创建规划的目录
```
runRemoteCmd.sh "mkdir -p /home/hadoop/data" all
```
### 启动并测试 hdfs
1.启动所有 Zookeeper 节点
```
runRemoteCmd.sh "/home/hadoop/app/zookeeper/bin/zkServer.sh start" all
```
2.启动所有 journalnode 节点
```
runRemoteCmd.sh "/home/hadoop/app/hadoop/sbin/hadoop-daemon.sh start journalnode" all
```
3.nn1 节点格式化 namenode
```
bin/hdfs namenode –format
```
4.nn1 节点格式化 zkfc
```
bin/hdfs zkfc -formatZK
```
5.nn1 节点启动 namenode
```
bin/hdfs namenode
```
6.namenode启动后nn2 节点同步 nn1 节点元数据信息，然后ctrl+c关闭namenode进程
```
bin/hdfs namenode –bootstrapStandby
nn2 同步完 nn1 节点信息之后， Ctrl+c 关闭 nn1 节点 namenode 进程。
```
7.关闭所有节点 journalnode
```
runRemoteCmd.sh "/home/hadoop/app/hadoop/sbin/hadoop-daemon.sh stop journalnode" all
```
### 一键启动 hdfs
```
sbin/start-dfs.sh
hdfs 启动之后可以通过如下命令查看 namenode 状态：
bin/hdfs haadmin -getServiceState nn1
bin/hdfs haadmin -getServiceState nn2
一键关闭 hdfs： sbin/stop-dfs.sh
```

### 查看namenode状态
```
bin/hdfs haadmin -getServiceState nn1
```