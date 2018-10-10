
[stream-tutorial](https://docs.confluent.io/current/quickstart/cos-docker-quickstart.html#cos-docker-quickstart)

```
# 创建主题
$ kafka-topics --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic users

# 查看主题列表
$ kafka-topics --list --zookeeper zookeeper:2181

# 查看主题详情
$ kafka-topics --zookeeper zookeeper:2181 --describe --topic users

# 增大分区数
$ kafka-topics --alter --zookeeper zookeeper:2181 --partitions 3 --topic users
```
