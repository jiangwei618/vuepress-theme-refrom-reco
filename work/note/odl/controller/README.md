**选主**  
odl集群主概念有多重：
    akka cluster 存在一个主；主要负责odl节点的集群管理，各个节点的加入、离线等

    数据库分片有主备之分，主要采用Raft算法实现选主。
        Candidate.class
**可用工具**
hawtio-app-2.6.0.jar: