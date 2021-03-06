title: Node进程
data: 2018-04-25 12:00:00
category: Node
tags: 
- process
- child_process

---

我们都知道 Node.js 是以单线程的模式运行的，但它使用的事件驱动来处理并发，这样有助于我们在多核 CPU 的系统上创建多个子进程，从而提高性能。

每个子进程总是带有三个流对象： child.stdin， child.stdout 和 child.stderr。 它们可能会共享父进程的 stdio 流，或者也可以是独立的被导流的流对象。

Node 提供了 child_process 模块来创建子进程，方法有：

- exec - child_process.exec 使用子进程执行命令，缓存子进程的输出，并将子进程的输出以回调函数参数的形式返回。

- spawn - child_process.spawn 使用指定的命令行参数创建新进程。

- fork - child_process.fork 是 spawn()的特殊形式，用于在子进程中运行的模块，如 fork('./son.js') 相当于 spawn('node', ['./son.js']) 。与spawn方法不同的是，fork会在父进程与子进程之间，建立一个通信管道，用于进程之间的通信。

#### 1.进程

- memoryUsage方法
- nextTick方法
- chdir
- cwd方法
- chdir方法
- exit方法
- kill方法
- uptime
- hrtime
- exit事件
- uncaughtException事件
- 信号事件

#### 2.子进程

- spawn
    - close
    - exit
    - error
    - kill
    - detached
- fork开启子进程
    - silent
    - 子进程与父进程共享http服务器
    - 子进程与父进程共享socket对象
- exec开启子进程
- execFile开启子进程

#### 3.cluster


--- ------------------------------------------------

**参考**
[菜鸟教程-进程](http://www.runoob.com/nodejs/nodejs-process.html)














