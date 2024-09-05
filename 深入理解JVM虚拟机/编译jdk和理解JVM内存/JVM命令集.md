## JVM命令集

#### 						Before JDK9						After JDK9

```java
1.查看GC基本信息：-XX:PrintGC						-Xlog:gc
2.查看GC详细信息:-XX:PrintGCDetails				  -Xlog:gc*
3.查看GC前后的堆，方法区可用容量变化：-XX:+PringHeadAtGC		-Xlog:gc+headp=debug
4.查看GC中用户线程并发时间以及停顿时间：-XX:+PringGCApplicationConcurrentTime						- 	-XX:+PringGCApplicationStpooedTime			-Xlog:safepoint
5.查看收集器Ergonomics机制（ 自动设置堆空间各分代区域大小、 收集目标等内容， 从Parallel收
集器开始支持） 自动调节的相关信息。 -XX:+PrintAdaptiveSizePolicy， -Xlog:gc+ergo*
6.查看熬过收集后剩余对象的年龄分布信息 -XX:PrintTenuring-Distribution		-Xlog:gc+age=trace
```

#### 		

![image-20240816230931487](C:\Users\lord2\AppData\Roaming\Typora\typora-user-images\image-20240816230931487.png)

![image-20240816230937978](C:\Users\lord2\AppData\Roaming\Typora\typora-user-images\image-20240816230937978.png)