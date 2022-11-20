# 记录我实现WebServer
reactor/procatar模式均有。
reactor 模式如下实现：
* 主线程：
    1. 监听和建立客户端的连接；
    2. 接收客户端的请求，创建一个任务，并把该任务放入任务队列；
    3. 通知分发线程。
* 分发线程
    1. 查看任务队列，看是否有请求任务？没有任务则继续睡觉，否则把任务取出来，然后分发给线程池；
    2. 线程池有空闲的线程，则把该任务交给空闲的线程处理，否则等待。
* 工作线程
    1. 执行任务
    2. 销毁任务

procatar 模式是用reactor模式模拟的：


总的来说：
* reactor模式中，主线程(I/O处理单元)只负责监听文件描述符上是否有事件发生，有的话立即通知工作线程(逻辑单元)，读写数据、接受新连接及处理客户请求均在工作线程中完成。通常由同步I/O实现。
* proactor模式中，主线程和内核负责处理读写数据、接受新连接等I/O操作，工作线程仅负责业务逻辑，如处理客户请求。通常由异步I/O实现。


WebServer主要有


## log




## 调试
我是在ubuntu上用vscode进行开发的，在调试过程中发现了一些问题。可以在命令行中使用以下代码开启管理员模式进而调试。
* OS VERSION : Ubuntu 20.04.2 LTS
* VScode Version : 1.73.1
```
sudo code --no-sandbox --disable-gpu-sandbox --user-data-dir=/root/.vscode/
```

