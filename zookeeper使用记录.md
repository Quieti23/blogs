查看版本信息  :echo stat|nc localhost 2181

sysm-dp启动报错：toptea.log
2017-11-09 09:57:00,299 [pool-1-thread-1] ERROR com.ai.toptea.sysm.cluster.ClusterManagerImpl (ClusterManagerImpl.java:597) - createPath fail: KeeperErrorCode = NodeExists for /sysm-dp/partition/0
org.apache.zookeeper.KeeperException$NodeExistsException: KeeperErrorCode = NodeExists for /sysm-dp/partition/0
        at org.apache.zookeeper.KeeperException.create(KeeperException.java:119)
        at org.apache.zookeeper.KeeperException.create(KeeperException.java:51)
        at org.apache.zookeeper.ZooKeeper.create(ZooKeeper.java:783)
        at org.apache.curator.framework.imps.CreateBuilderImpl$11.call(CreateBuilderImpl.java:721)
        at org.apache.curator.framework.imps.CreateBuilderImpl$11.call(CreateBuilderImpl.java:704)
        at org.apache.curator.RetryLoop.callWithRetry(RetryLoop.java:108)
        at org.apache.curator.framework.imps.CreateBuilderImpl.pathInForeground(CreateBuilderImpl.java:701)
        at org.apache.curator.framework.imps.CreateBuilderImpl.protectedPathInForeground(CreateBuilderImpl.java:477)
        at org.apache.curator.framework.imps.CreateBuilderImpl.forPath(CreateBuilderImpl.java:467)
        at org.apache.curator.framework.imps.CreateBuilderImpl.forPath(CreateBuilderImpl.java:44)
        at com.ai.toptea.sysm.cluster.ClusterManagerImpl.createPath(ClusterManagerImpl.java:594)
        at com.ai.toptea.sysm.data.KafkaReadTask.addPartition(KafkaReadTask.java:162)
        at com.ai.toptea.sysm.data.KafkaReadTask.reassignPartition(KafkaReadTask.java:148)
        at com.ai.toptea.sysm.data.KafkaReadTask$1.onValueChange(KafkaReadTask.java:105)
        at com.ai.toptea.sysm.cluster.NodeAttachmentListener.onEvent(NodeAttachmentListener.java:86)
        at com.ai.toptea.sysm.cluster.ClusterManagerImpl.lambda$handleNodeEvent$1(ClusterManagerImpl.java:208)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)

原因：之前节点的path没有释放
           
解决方法：1.停掉所有sysm-dp节点；
                  2.登录zk  rmr /sysm-dp
                    [toptea@vgabomcweb01 zookeeper]$bin/zkCli.sh 
                    Connecting to localhost:2181
                    2017-11-09 10:03:02,829 [myid:] - INFO  [main:Environment@100] - Client environment:zookeeper.version=3.4.5-cdh5.5.0-               -1, built on 11/09/2015 20:27 GMT

                    [zk: localhost:2181(CONNECTED) 0] rmr /sysm-dp

                   3.启动sysm-dp