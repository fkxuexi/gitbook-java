### 1、sleep

- 1、为Thread的静态方法

- 2、不放弃 monitor的锁，

- 3、sleep 醒来直接进去就绪状态

- 4、不能被notify()、notifyAll()唤醒，不能用于线程之间的通信

### 2、wait

- 1、定义在Object中，只能在同步代码块中使用

- 2、可以被notify()、notifyAll()唤醒