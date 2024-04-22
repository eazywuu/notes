## server端

### 连接器

**怎么连接 ?**

应用层使用自定义的网络协议，传输层在通过tcp三次握手

为什么不使用http？

1. http协议的报文过于冗余

使用池化技术来限制客户端连接，不能无限制的连接sever。

管理连接与权限校验：认证，鉴权

### 分析器

### 执行器 

> 调用存储引擎接口

## 存储引擎

> This is a message.

> 海量数据时按列存储更多，如Apache Doris，这样查某个字段时，直接按字段列扫描

按行存储。

通过和操作系统交互，达到和磁盘交互的目的。

Buffer Pool 缓存池：对数据库操作时，会先在此处操作，然后定时同步磁盘，减少io

Redo Log Buffer 写redo日志。

## 杂项

缺页中断

redolog和binlog

索引选择异常和处理

record-lock，gap-lock，行锁，next-key lock，

乐观锁：MVCC -》udolog + 两个隐藏字段 TRX_ID，UNDO_LOG_PTR，

悲观锁：pv操作

java乐观锁：cas，会有aba问题，通过加版本号解决。

QPS突增问题

**mysql性能问题**

短连接风暴

![image-20220916220708562](C:\Users\mycomputer\AppData\Roaming\Typora\typora-user-images\image-20220916220708562.png)

少写慢sql：设置IDLE timeout

![image-20220916221030355](C:\Users\mycomputer\AppData\Roaming\Typora\typora-user-images\image-20220916221030355.png)

![image-20220916221820971](C:\Users\mycomputer\AppData\Roaming\Typora\typora-user-images\image-20220916221820971.png)![image-20220916221828761](C:\Users\mycomputer\AppData\Roaming\Typora\typora-user-images\image-20220916221828761.png)