##系统虚拟化学习指南

### 0. 前置知识
#### Linux基本使用 
+ 简介和系统安装
+ 日常使用
	+ 文件 目录 权限 用户
	+ 网络基本配置
		+ ip
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
+ 多线程编程
	+ pthreads API
+ 异步IO编程接口
	+ Linux AIO
	+ eventfd
	+ epoll
	

> 参考资料：

> 1. 《Linux系统编程》 Robert.Love
> 2. 《Unix环境高级编程》 Stevens & Rago
> 3. [POSIX Threads Programming](https://computing.llnl.gov/tutorials/pthreads/)

#### x86虚拟化基本原理
+ 虚拟化技术基础
	+ 可虚拟化架构
	+ 陷入-模拟
	+ Hypercall
+ 虚拟化技术的层次
	+ 硬件抽象层上的虚拟化
		+ 硬件接口和ISA
		+ 虚拟化和仿真
	+ 操作系统层上的虚拟化
		+ OS接口和system call
		+ 基于容器的虚拟化
	+ 库函数层上的虚拟化
	+ 编程语言层上的虚拟化
		+ 高级语言虚拟机
+ 从全虚拟化和半虚拟化到硬件虚拟化
	+ CPU虚拟化
	+ 内存虚拟化
	+ I/O设备虚拟化
+ 虚拟机监控器
	+ Xen体系结构
		+ Para-virtualization
		+ PV on HVM
		+ PVH
	+ KVM体系结构
		+ virtio
			
> 参考资料：

> 1. [《系统虚拟化：原理与实现》Intel & 复旦](http://vdisk.weibo.com/s/z8gP5wLggZHwa) 之第1、3章
> 2. [An Introduction to Virtualization](http://www.kernelthread.com/publications/virtualization/)
> 2. [An Introduction to Full Virtualization With Xen (Part 1)](http://www.linux.com/news/enterprise/systems-management/655446-an-introduction-to-paravirtualization-and-xen/)
> 3. [Intro to the Paravirtualization Spectrum With Xen (Part 2)](http://www.linux.com/news/enterprise/systems-management/658784-the-spectrum-of-paravirtualization-with-xen-part-2/)

#### 存储基础
+ 块存储	
	+ IPSAN和FCSAN
	+ 硬盘性能测试
+ 文件系统
	+ Linux虚拟文件系统	
	+ 稀疏文件
+ 虚拟磁盘
	+ raw格式和loop设备
	+ qcow2格式
	+ Copy-On-Write原理
	+ 虚拟机镜像管理

> 参考资料：
> 
> 1. [块存储的世界](https://www.ustack.com/blog/block-storage-overview/)
> 2. [如何测试云硬盘](https://www.ustack.com/blog/how-benchmark-ebs/)
> 3. [Linux 虚拟系统文件交换器剖析](http://www.ibm.com/developerworks/cn/linux/l-virtual-filesystem-switch/)
> 4. [Linux文件空洞与稀疏文件](http://ilinuxkernel.com/?p=1417)
> 5. 《Qcow2格式调研报告》赵祯龙
> 6. 《大话存储2》第16章
> 7. [KVM镜像管理利器-guestfish使用详解](http://xiaoli110.blog.51cto.com/1724/1568307/)
> 8. [挂载KVM Guest操作系统磁盘](http://www.cnblogs.com/wang_yb/p/3980599.html)

#### 虚拟网络
+ TUN/TAP设备
+ 虚拟网桥
+ Open vSwitch

> 参考资料：
> 
> 1. 《Linux内核精髓》高桥浩和 之第四章
> 2. [Linux 上的基础网络设备详解](http://www.ibm.com/developerworks/cn/linux/1310_xiawc_networkdevice/)
> 3. [ovs官网介绍](http://openvswitch.org/)
> 4. [Linux 中的虚拟网络](https://www.ibm.com/developerworks/cn/linux/l-virtual-networking/)

### 2. oVirt技术路线调研
+ 系统架构
+ 版本演进
+ 组件版本
	+ Qemu
	+ Kernel、KVM、virtio backend
	+ libvirt
	+ Windows Guest Tool

+ 虚拟机管理
	+ 虚拟机迁移
		+ 跨主机，不跨存储
		+ 跨存储，不跨主机
		+ 跨主机，跨存储
	+ 模板管理
	+ 快照管理

+ 存储管理
	+ SAN和NAS的使用方式
	+ 分布式存储支持进展 

+ 网络管理
	+ linux网桥的使用方式
	+ 如何集成openvswitch

+ 管理节点HA方案

> 参考资料：

> 1. [oVirt官网](http://www.ovirt.org/Home)
> 2. [RHEV官方手册](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Virtualization/)

### 3. Qemu和KVM

+ qemu-kvm的基本使用
	+ 编译和安装
	+ 开发环境搭建
	+ 基本客户机参数配置
		+ CPU和内存
		+ 存储配置
		+ 网络配置
		+ 图形显示
	+ 高级客户机参数配置
		+ virtio
			+ virtio_balloon 
			+ virtio_net 
			+ virtio_blk 
			+ vhost技术
		+ 设备直接分配
		+ 内存过载使用
			+ KSM
			+ balloon
			+ 内存交换
		+ 热拔插
			+ PCI设备
			+ CPU和内存
	+ 虚拟机热迁移
	+ 性能优化方法
+ Intel硬件虚拟化技术
	+ Vt-x基本原理
		+ VMCS、VMX操作模式和指令集
		+ 中断虚拟化
	+ EPT基本原理
	+ Vt-d基本原理
		+ IOMMU和DMA重映射
		+ 设备直接分配和SR-IOV
+ 内核中的KVM
	+ KVM模块
		+ 系统抽象
			+ System、VM、VCPU
		+ 接口设备/dev/kvm和API
	+ virtio系列模块
		+ 体系结构
		+ virtio总线、ring、balloon
		+ virtio blk、net设备驱动
		+ vhost
	+ 调优方法


> 参考资料：

> 1. 《KVM虚拟化技术：实战与原理解析》
> 2. [《系统虚拟化：原理与实现》Intel & 复旦](http://vdisk.weibo.com/s/z8gP5wLggZHwa) 之第2、5章
> 3. 《Linux内核精髓》高桥浩和 之第五章
> 4. [KVM官网文档](http://www.linux-kvm.org/page/Main_Page)
> 5. [KVM内核模块API](https://www.kernel.org/doc/Documentation/virtual/kvm/api.txt)
> 6. [Vhost Architecture](http://luoye.me/2014/08/22/vhost/)


### Appendix A： Linux内核编程
+ 简单模块编写
+ 内核基本数据结构
+ 内存管理
+ 内核同步方法
+ 中断和下半部
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
+ KVM
	+ [luoye 个人博客](http://luoye.me/)
	+ [smilejay 个人博客](http://smilejay.com/)
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




