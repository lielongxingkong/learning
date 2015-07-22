## 分布式存储学习指南 (20150718)

### 0. 前置知识
#### Linux基本使用 
+ 简介和系统安装
+ 日常使用
	+ 文件 目录 权限 用户
	+ 网络基本配置
		+ TCP/IP
		+ 防火墙
			+ iptables
			+ **firewalld**
	+ bash和shell基本使用
+ 系统管理
	+ 基于CentOS7，对比CentOS6
	+ 源码与包管理
		+ yum
		+ rpm和rpmbuild 
	+ 进程和系统服务管理
		+ Sysvinit
		+ Upstart
		+ **Systemd**

> 参考资料：
> 
> 1. 《鸟哥的Linux私房菜（基础学习篇）》之第一部分、第二部分、第三部分 + 20、22、23章 
> 
> 2. [RHEL官方手册](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/)
> 3. [浅析 Linux 初始化 init 系统，第 1 部分: sysvinit](https://www.ibm.com/developerworks/cn/linux/1407_liuming_init1/)
> 4. [浅析 Linux 初始化 init 系统，第 2 部分: UpStart](http://www.ibm.com/developerworks/cn/linux/1407_liuming_init2/)
> 5. [浅析 Linux 初始化 init 系统，第 3 部分: Systemd](http://www.ibm.com/developerworks/cn/linux/1407_liuming_init3/)

#### 开发工具
+ vim
+ **git & git-flow**
+ markdown 

> 参考资料：

> 1. [《Pro Git》](http://git.oschina.net/progit/)
> 2. [一个成功的git模型](http://nvie.com/posts/a-successful-git-branching-model/)
> 3. [markdown语法说明](http://www.appinn.com/markdown/)
> 4. [简明vim练级攻略](http://coolshell.cn/articles/5426.html)


#### 开发语言

+ **python**
	+ virtualenv
	+ setuptools
	+ pdb
	+ 与shell交互
	+ pytest和mock


+ C语言
	+ gcc
	+ gdb
	+ 编译、链接、加载流程
	+ 函数调用、栈帧组织
	+ 内存管理
	+ 常用Linux系统调用使用方法
	
> 参考资料：

> 1. 《Python基础教程》
> 2. [啄木鸟社区](http://wiki.woodpecker.org.cn/moin/)
> 2. 《C专家编程》


### 1. 基础知识
#### Linux系统编程
+ 常用系统调用原理
+ 文件I/O
+ 标准库I/O
+ 非阻塞IO和异步IO
+ I/O多路复用
	+ select、poll和epoll
+ 多线程编程
	+ pthreads API
	

> 参考资料：

> 1. 《Linux系统编程》 Robert.Love
> 2. 《Unix环境高级编程》 Stevens & Rago
> 3. [POSIX Threads Programming](https://computing.llnl.gov/tutorials/pthreads/)


#### 存储基础
+ 磁盘
	+ LBA
	+ 分区和分区表
		+ MBR和GPT
	+ 硬盘接口
	+ 磁盘的并发度
	+ SSD
+ RAID
	+ RAID 0/1/01/10/5
+ LVM
	+ device mapper in Linux
+ SAN
	+ SCSI体系结构
	+ IP-SAN
	+ FC-SAN
+ 块设备性能测试
	+ IOPS
	+ Bandwidth
	+ 性能测试工具
		+ dd、fio、iometer、iozone等
+ Linux IO stack
	+ 通用块设备层与bio
+ 文件系统
	+ 文件IO和标准库
		+ 系统调用
		+ 输入输出流
	+ Unix文件观
		+ 设备与文件
		+ 块设备到文件 
			+ sysfs与udev
		+ 文件到块设备
			+ loop设备
		+ 块设备与文件的联系
	+ Linux VFS体系结构	
		+ 实例分析1: FUSE
		+ 实例分析2: NFS
		+ 实例分析3: procfs
	+ 元数据与日志文件系统
		+ 实例分析4：Ext2与Ext3
+ 分布式存储
	+ RPC
	+ Master-Slave
	+ 一致性哈希
		+ 虚拟节点
		+ 实例分析5: Swift
	+ 复制和一致性
		+ CAP原理
	+ 分布式事务
		+ 2PC
		+ 3PC
		+ Paxos
	+ 对象存储体系结构
		+ NAS和SAN架构分析
		+ 概念和体系结构
	+ 分布式文件系统
		+ 概念和体系结构
		+ 实例分析6: HDFS


> 参考资料：
> 
> 1. [块存储的世界](https://www.ustack.com/blog/block-storage-overview/)
> 2. [Linux 虚拟系统文件交换器剖析](http://www.ibm.com/developerworks/cn/linux/l-virtual-filesystem-switch/)
> 3. 《大话存储2》
> 4. [Linux-IO Target介绍(一)](https://www.ibm.com/developerworks/community/blogs/5144904d-5d75-45ed-9d2b-cf1754ee936a/entry/linux_io_target%25e4%25bb%258b%25e7%25bb%258d_%25e4%25b8%2580?lang=en)
> 5. [Linux-IO Target介绍(二)](https://www.ibm.com/developerworks/community/blogs/5144904d-5d75-45ed-9d2b-cf1754ee936a/entry/april_11_2014_12_58_am?lang=en)
> 6. [Linux SCSI子系统剖析](http://www.ibm.com/developerworks/cn/linux/l-scsi-subsystem/)
> 7. 《OCFS2系列调研文档》张俊
> 8. [Linux文件空洞与稀疏文件](http://ilinuxkernel.com/?p=1417)
> 9. [分布式系统工程实践](https://nfil.es/a/DfuDrV/)
> 10. [构建大型云计算平台分布式技术的实践](http://www.infoq.com/cn/news/2014/07/aliyun-distributed)


#### 系统虚拟化基本原理
+ 虚拟化技术基础
+ 从全虚拟化和半虚拟化到硬件虚拟化
	+ CPU虚拟化
	+ 内存虚拟化
	+ I/O设备虚拟化
+ 虚拟机监控器
	+ Xen和KVM体系结构
	+ KVM体系结构
	+ PV on HVM
+ 虚拟磁盘
	+ raw格式
	+ qcow2格式
		+ Copy-On-Write原理
	+ 虚拟机镜像管理
	+ Linux稀疏文件
	+ qdisk
	
			
> 参考资料：

> 1. [《系统虚拟化：原理与实现》Intel & 复旦](http://vdisk.weibo.com/s/z8gP5wLggZHwa) 之第1、3章
> 2. [KVM镜像管理利器-guestfish使用详解](http://xiaoli110.blog.51cto.com/1724/1568307/)
> 3. [挂载KVM Guest操作系统磁盘](http://www.cnblogs.com/wang_yb/p/3980599.html)
> 4. 《Qcow2格式调研报告》赵祯龙
> 5. [如何测试云硬盘](https://www.ustack.com/blog/how-benchmark-ebs/)



### 2. Ceph
+ 体系结构
+ Rados
+ librbd


> 参考资料：


### Appendix A： Linux内核编程
+ 简单模块编写
+ 内核基本数据结构
+ 进程模型
+ 内存管理
+ 内核同步方法
+ 中断和下半部
	+ Linux中断体系结构
	+ 中断上下文
	+ 软中断
	+ tasklet
	+ 工作队列
+ 设备模型和sysfs
+ PCI总线和设备驱动
+ 块设备和网络设备驱动
+ 虚拟文件系统

> 参考资料：
> 
> 1. 《Linux设备驱动》
> 2. 《Linux内核设计与实现》 Robert.Love
> 3. 《Linux内核精髓》高桥浩和
> 4. 《深入理解Linux内核》

### Appendix B： 一些网络资料
+ 存储
	+ [EMC存储基础知识](https://community.emc.com/message/740198#740198)
+ 云计算
	+ [UnitedStack官博](https://www.ustack.com/blog/)
	+ [Mirantis官博](https://www.mirantis.com/blog/)

+ Linux
	+ [红帽官方文档库](https://access.redhat.com/documentation/en-US/)
	+ [内核源码搜索](http://lxr.free-electrons.com)
	+ [Linux内核之旅](http://www.kerneltravel.net)
	+ [LWN.net](http://lwn.net)
	+ [IBM文档库](https://www.ibm.com/developerworks/cn/linux)
	+ [eudyptula-challenge](http://eudyptula-challenge.org)




