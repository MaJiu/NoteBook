### Java 多线程

线程之间的共享变量要使用 `volatile` 关键字

`stop` 方法已经废除

**守护线程**

在 JVM 中，所有**非守护线程**都执行完毕后，无论有没有守护线程，虚拟机都会自动退出

守护线程不能持有任何需要关闭的资源，虚拟机退出时，守护线程没有任何机会来关闭文件

`setDaemon(true)`把该线程标记为守护线程

`synchronized` 框中的代码为 **临界区**

可重入锁

[synchronized锁定的到底是什么？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/57794716?sort=created)

[synchronized详解 -l 三分恶 - 博客园 (cnblogs.com)](https://www.cnblogs.com/three-fighter/p/14396208.html)