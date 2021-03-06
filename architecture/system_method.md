## 系统方法
1. 通信
    1. 协议设计
        1. 概念
            1. 实体
            2. 对等点
        2. 要素
            1. 语法：数据与控制信息的结构与格式
            2. 语义：需要发出何种控制信息，完成何种动作，做出何种响应
            3. 时序：事件实现的顺序
        3. 核心问题
            1. 差错控制
                1. 校验
                    1. 丢弃
                    2. 纠错
            2. 流量控制
            3. 分段与重装
                1. 存储-转发
                2. 线速转发
            4. 复用与分用
                1. 分时
                2. 分频
                3. 空分
                4. 码分
            5. 连接建立与释放
                1. 面向连接
                2. 面向非连接
    2. 通信方式
        1. 按照时序
            1. 同步通信
            2. 异步通信
        2. 按照位宽
            1. 串行通信
            2. 并行通信
        3. 序列化
        4. 分布式消息
            1. 消息队列
                1. 消息、事件驱动
            2. RPC
                1. Stub伪过程
                2. 传参
                3. 字节序
            3. RMI
2. 互联
    1. 网络体系结构：各层协议的集合
    2. 拓扑
        1. 总线
            1. 分类
                1. 片内总线
                2. 系统总线
                    1. 地址总线
                    2. 数据总线
                    3. 控制总线
                3. 通信总线
            2. 传输周期
                1. 申请分配
                2. 寻址
                3. 传数
                4. 结束
        2. 点对点
            1. ATA、virtio
        3. 总线型
            1. PCI
        4. 星型 交换
            1. SAS、PCI
        5. 链式
            1. SCSI
        6. 环状
            1. FC
        7. 网格状
            1. mesh
        8. 网状
            1. IP
    3. 几个基本问题
        1. 定址 我在哪里，要到哪去
        2. 路由 怎么去
            1. 要求
                1. 适应规模
                2. 一致、收敛、防环
            2. 寻路
                1. 基于总线
                    1. 广播
                2. 基于树
                    1. 最小生成树
                3. 基于图
                    1. 基于距离矢量
                        1. 泛洪邻居状态
                        2. Bellman-Ford算法
                    2. 基于链路状态
                        1. 泛洪全局路由
                        2. Dijkstra算法
    4. 互连系统
        1. 多计算机系统 60年代中
            1. 多台分散的处理机组成的系统
            2. 举例
                1. IO处理机
                2. 前端处理机        2. 多处理机系统 70年代
            1. 多个处理机构成的单机        3. 网络系统 70年代        4. 分布式系统 78年左右
3. 命名
4. 分布式系统
    1. 分布式系统架构
        1. 系统目标
            1. 集成
            2. 资源共享
            3. 协同工作
            4. 任务并行
            5. 可靠与容错
        2. 分布式系统主要特征
            1. 一组由网络互联的、自治的计算机和资源
            2. 资源为用户所共享
            3. 可以集中控制，也可以分布控制
            4. 计算机可以同构，也可以异构 
            5. 分散的地理位置
            6. 分布式故障点
            7. 没有全局时钟
            8. 大多数情况下没有共享内存 
            9. 透明性
        3. 基本模型
            1. 集中式模型
                1. Client-Server
            2. 非集中式模型
                1. Peer-to-Peer
                    1. 结构化
                        1. 形式
                            1. 环
                            2. 网格
                            3. 树
                        2. 分布式哈希表 DHT
                            1. Chord
                            2. Pastry
                            3. CAN
                    2. 非结构化
    2. 分布式进程
        1. 进程迁移
    3. 复制
        1. 目的
            1. 可靠性
                1. 主备
            2. 性能
                1. 负载均衡
        2. 方式
            1. 数据级别
                1. 多副本
    4.  一致性
        1. 一致性协议
            1. CAP原理
        2. 一致性模型
            1. 强一致性
                1. 分布式事务
                    1. 2PC
                    2. 3PC
                    3. Paxos
            2. 弱一致性
                1. 最终一致性
5. 关注点
    1. 扩展性
        1. 范围
            1. 规模
                1. 没有任何机器拥有系统完整信息
                2. 只根据本地信息决策                3. 不会出现单点故障崩溃                4. 没有全局性时钟
            2. 地域
                1. 广域网同步与延迟                2. 不可靠通信                3. 集中组件导致资源浪费
            3. 管理
                1. 跨管理域                2. 资源使用                3. 权限与安全
                4. 配置与管理
        2. 扩展技术
            1. 隐藏通信等待时间
            2. 分布 
                1. Sharding
            3. 复制
    2. 可用性
        1. 异步
        2. 复制
    3. 可靠性
        1. 复制
        2. 版本
    4. 一致性
    5. 负载均衡
    6. 过载保护
    7. 性能
        1. 优化方法
            1. 缓存
            2. 复制
            3. 延迟计算与路径优化
            4. 数据预读
            5. 异步
            6. 轮询与通知
            7. 内存池
            8. 模块化
            9. 硬件加速
        2. 性能排查和调优
            1. 性能指标
            2. 性能测试
    8. 版本管理
        1. 基于快照
            1. 写时复制技术
                1. 写前复制
                2. 写时复制
        2. 基于增量迭代
    9. 容错
        1. 故障分类
            1. 瞬时故障
                1. 断电
                2. 断网
                3. 误操作
            2. 永久故障
                1. 损坏
                2. 灾难
        2. 故障处理
            1. 故障隔离
            2. 故障修复
                1. 可修复
                    1. 不修复
                    2. 日志重放
                    3. 回退快照
                2. 不可修复
                    1. 置为废弃
                    2. 启用副本

```
分布式系统参考资料（未完成）：
1. 《分布式系统原理与范型》书 Andrew S.Tanenbaum
2. 《大规模分布式存储系统：原理解析与架构实战》书 杨传辉  
3. 《分布式系统工程实践》(https://nfil.es/a/DfuDrV/)
4. 《构建大型云计算平台分布式技术的实践》博客 http://www.infoq.com/cn/news/2014/07/aliyun-distributed
5. 《Distributed systems for fun and profit》电子书 http://book.mixu.net/distsys/single-page.html
```
