# Go 调度器

## 线程与Goroutine

go语言的调度器通过使用与CPU数据相等的线程减少线程频繁切换的内存开销



G-M-P模型

基于信号的抢占式调度

## 为什么需要调度器

方便高并发线程的编写。

一个线程在进行阻塞操作时，调度器会将当前线程的其他goroutine移交到其他线程中继续执行，从而避免整个程序的阻塞。

同时，也增加了程序的复杂性。一个Goroutine既要包含执行代码，也要包括用于执行代码的栈和PC、SP指针。

## 调度器解决了什么问题

### 栈管理

创建栈时，只分配一块比较小的内存。栈空间不足时，重新分配新的栈空间。避免频繁的内存分配和释放

### 抢占式调度

如果一个goroutine一直占用cpu，长时间没有被调度过，就会被runtime抢占掉，把CPU时间交给其他goroutine。



## 参考

https://colobu.com/2017/05/04/go-scheduler/

http://ga0.github.io/golang/2015/09/20/golang-runtime-scheduler.html