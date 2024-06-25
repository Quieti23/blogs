kafka topic扩容
bin/kafka-topics.sh --alter --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181 --topic sysm-data-ccp --partitions 20       

查询kafka topic列表
bin/kafka-topics.sh --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181 --list       

查询kafka topic分区
bin/kafka-topics.sh --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181 --topic sysm-data-ccp --describe 查询kafka topic分区

bin/kafka-console-producer.sh --broker-list 135.10.106.35:135.10.106.36:9092，135.10.106.37:9092，135.10.106.38:9092，135.10.106.40:9092 --topic  ccp-task-fd

bin/kafka-console-consumer.sh --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181  --topic sysm-data-ccp --from-beginning


kafka删除topic后新建topic：
1.killKafka进程,kafka删除topic(bin/kafka-topics.sh --delete --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181 --topic sysm-moEvent)
2.删除所有kafka消息数据：/data/toptea/opt/app/kafka_2.11-0.10.1.0/kafka-logs/*
3.删除zookeeper注册的Kafka topic节点（/brokers/topics）
4.启动所有集群Kafka应用（bin/kafka-server-start.sh -daemon config/server.properties  启动命令）
5.创建topic（bin/kafka-topics.sh --create --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181 --replication-factor 5 --partitions 20 --topic sysm-moEvent ）
6.检查是否生产消费数据正常（
    1.生产数据（c）
    2.消费数据（bin/kafka-console-consumer.sh --zookeeper 135.10.106.29:2181,135.10.106.30:2181,135.10.106.31:2181,135.10.106.32:2181,135.10.106.33:2181  --topic sysm-data-ccp--from-beginning）
）
