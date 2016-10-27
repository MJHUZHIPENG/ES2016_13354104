# 死锁

## 一、截图

![deadlock](http://a2.qpic.cn/psb?/V11CqRKq4GZb0Y/SekU*SYAg3*hBTke.SrUFFhnAxCT90vBgKRxRESBIv4!/b/dAkBAAAAAAAA&bo=4wLiAQAAAAADByA!&rf=viewer_4)
*deadlock*
***

## 二、产生死锁必要条件
* 互斥条件：一个资源每次只能被一个进程使用
* 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放
* 不剥夺条件:进程已获得的资源，在末使用完之前，不能强行剥夺
* 循环等待条件:若干进程之间形成一种头尾相接的循环等待资源关系

## 三、产生死锁的解释
t.start()调度之后，线程t被插入调度队列里面去排队，此时同时发生两件事情：

* 线程t 默默排队，等待轮到它。接着跑run()里面的代码，也就是b.methodB(a)这句
* count不断减一,一直减到0。接着跑a.methodA(b)

假如count调到刚好和t 等待时间差不多，b.methodB(a)和a.methodA(b)就会同时调度，因为synchronized的关系，a和b两个对象一直占用对方请求的资源而不释放，从而产生死锁。