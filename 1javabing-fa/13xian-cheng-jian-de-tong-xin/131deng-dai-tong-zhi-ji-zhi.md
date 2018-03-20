#### 1、使用标志变量+轮询的方法

使用volatile标志标量，然后在通过while进行轮询判断进行线程间的通讯，但是这种方法需要不简单的轮询耗费资源


#### 2.等待通知机制的实现：

- wait/notify

方法wait是使当前的执行的代码进行等待，且释放cpu和锁等资源，直到接到通知或者被中断为止。在调用前wait方法必须要获得锁才可以(所以wait方法要被使用在同步块中);

方法notify也是要活动锁才可以执行，所以也必须在同步代码块中执行，在执行notify后当前的notify对象不会立即释放锁，必须要等待notify代码执行完成之后才会释放锁，即退出synchronized之后wait方法才可以获取锁
