## VSan学习指南(141019)
---

### 1. 前置知识 

#### Linux基本使用 
+ 简介和安装
+ 日常使用
	+ 文件 目录 权限 用户
	+ 网络基本配置 ip 防火墙
	+ bash和shell
+ 系统管理
	+ 源码与包管理 
	+ 进程和系统服务管理
	+ Sysvinit Upstart Systemd


>参考资料：《鸟哥的Linux私房菜（基础学习篇）》之第一部分、第二部分、第三部分 + 20、22、23章  
Sysvinit Upstart Systemd的资料可在网上搜集

>**练习1：配置节点间ssh无密码访问**  
>**练习2：配置内网CentOS 6.5的yum源**  
>**练习2ex：基于nginx反向代理实现yum源http服务的负载均衡，并根据tracing数据验证不同的负载均衡策略**


#### 开发相关
+ 开发工具
	+ vim
	+ Eclipse
	+ **git & git-flow**
	+ markdown 
	

>参考资料：《Pro Git中文版》之1-3章  和  [一个成功的git模型](http://nvie.com/posts/a-successful-git-branching-model/)


>**练习3：完成 [Git Immersion](http://gitimmersion.googol.im/index.html)**


```	
技术交流内容: 
	《Sysvinit、Upstart、Systemd介绍 part1》
	 一、三个系统的介绍
	     1. 这三个系统的是干什么的
	     2. Sysvinit介绍，存在什么问题
	     3. Upstart介绍，如何解决Sysvinit存在的问题，如何做到与前者接口的兼容
	     4. Upstart本身存在什么问题，Systemd的特点
	 二、Redhat 6的启动流程简介，从BIOS加电自检到X-Window启动
	《Sysvinit、Upstart、Systemd介绍 part2》
	 一、三个系统的使用方法，可参考Redhat官方文档
	     1. Sysvinit、Upstart的命令及使用方法，CentOS 6环境下演示
	     2. Systemd的命令及使用方法，CentOS 7环境下演示
	     3. Sysvinit脚本解析，以httpd为例
	 二、Systemd并发启动原理
	     1. 如何解决socket依赖
	     2. 如何解决D-Bus依赖
	     3. 如何解决文件系统依赖
```



### 2. 存储基础
+ 块存储	
	+ 按块的访问方式
		+ 随机访问
		+ 顺序访问
	+ 磁盘
		+ LBA
		+ 分区和分区表
			+ MBR
				+ 分区扩展
			+ GPT
		+ 硬盘接口
		+ 磁盘的并发度
	+ RAID
		+ RAID 0/1/01/10/5
	+ LVM
		+ device mapping
	+ SAN
		+ IPSAN
		+ FCSAN
	+ 块设备性能测试
		+ IOPS
		+ Bandwidth
+ 文件系统
	+ 文件IO和标准库
		+ 系统调用
		+ 输入输出流
	+ Unix文件观与Plan 9
	+ Linux VFS体系结构	
		+ 实例分析1: FUSE
		+ 实例分析2: NFS
		+ 实例分析3: procfs
	+ 元数据与日志文件系统
		+ 实例分析4：Ext2
		+ 实例分析5：Ext3
+ 设备与文件
	+ 块设备到文件 
		+ sysfs与udev
	+ 文件到块设备
		+ loop设备
	+ 块设备与文件的联系
+ 对象存储 上
	+ NAS和SAN架构分析
	+ 概念和体系结构



	
	
>**练习4：虚拟磁盘性能测试**  

```
1. 学习以下几篇文章
块存储的世界 https://www.ustack.com/blog/block-storage-overview/
如何测试云硬盘 https://www.ustack.com/blog/how-benchmark-ebs/
构建大型云计算平台分布式技术的实践 http://www.infoq.com/cn/news/2014/07/aliyun-distributed

2. 掌握dd、fio、iometer、iozone等性能测试工具
工具安装
参数配置
结果分析

3. 在www.ustack.com上复现“如何测试云硬盘”中的结果
并验证docs.ustack.com/uos_services/block_storage.html中提到的SLA

4. iVirtual vSAN虚拟磁盘性能测试

5. 根据以上内容撰写unitedstack云硬盘测试报告，以及iVirtual虚拟磁盘性能测试方案
```


> 练习5：利用FUSE实现一个文件系统，并实现功能
> 
> 1. 将xen中开启的虚拟机转化为文件列表，并通过ls查看Domain 0中开启的虚拟机
> 2. 删除文件，关闭对应的虚拟机
> 3. 读文件，获得虚拟机的id



### 3. 分布式系统基础
+ RPC
+ Master-Slave
+ 一致性哈希
	+ 虚拟节点
	+ 实例分析: Swift
+ 复制和一致性
	+ CAP原理
+ 分布式事务
	+ 2PC
	+ 3PC
	+ Paxos
+ 分布式文件系统
	+ 概念和体系结构
	+ 原理
	+ 实例分析: HDFS
+ 大话云存储


### 4. Ceph相关
+ 体系结构
+ Rados
+ librbd

### 5. Xen相关
+ Xen体系结构
+ PV on HVM
+ qdisk

---

### ChangeLog
+ 140924 创建
+ 141014 添加练习2ex，添加技术交流内容
+ 141019 添加练习4，练习5，更新存储基础和分布式系统基础