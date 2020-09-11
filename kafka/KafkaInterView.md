####1、Kafka中的ISR、AR、OSR代表什么？ISO伸缩指的是什么？
* AR:所有副本的集合
* ISR:所有与Leader副本保持一定程度上一致的副本集合（包含了Leader副本）
* OSR:与Leader副本滞后过多的副本集合（不包含Leader副本）
* ISR伸缩：Leader副本会监视和跟踪ISR集合中的所follower副本，若follower副本滞后过多或者失效了，Leader副本就会将其从ISR集合中剔除；
若OSR集合中有follower副本追赶上了Leader副本，会将其移动到ISR集合中；若Leader副本出现故障，需要重新进行选举Leader,此时只会从ISR集合
中选举，OSR中的默认是不会参与选举的

####2、Kafka中的HW、LEO、LSO、LW分别代表什么？
* HW：High WaterMark 高水位---ISR集合中最小的LEO为HW，消费者只能拉取到HW之前的消息。
* LEO: Log End Offset ----每个分区最后一条消息的下一个位置，也是下一条消息待写入的位置。
* LW：Low WaterMark ----AR集合中最小的logStartOffset的值。
* LSO：与事务相关，事务中未完成的事务中的第一条消息的位置。

####3、
``````