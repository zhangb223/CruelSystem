#动机
由于现有的文件存储系统已经无法满足Google目前和未来的需求
1.文件系统的的组成部分失效高于预期
2.在传统标准意义上我们的文件过于庞大
3.多数文件的改变是通过增量而不是修改存量的方式
#架构
GFS集群的架构是使用一个主服务器和多个块服务器，客户端从主服务器查询到数据所在的块服务器。
#存储过程、修改过程
每个文件被分成固定大小的块，每一个块被64位的块具柄标记，当块产生的时候，并通过这个具柄定位到块进行修改。
#可靠性
为了保证可靠性每个块都被存储在多个块服务器上做备份，默认情况下会做三个备份。
#主节点
主节点用来保存元数据，包括命名空间、访问控制信息、从文件到块的映射信息和块的当前位置。
主节点还负责全系统的活动，例如 对孤儿块的垃圾收集、对块服务器的心跳检测。

