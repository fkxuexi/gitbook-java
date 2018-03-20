### 1、synchronized和volatile的区别

- volatile 只能修饰变量，而synchronized则可以修饰方法

- volatile 更加的轻量级，

- volatile 不会发生阻塞，synchronized则会发生阻塞

- volatile 只保证可见性，不保证原子性

ps：各自解决的点不同

- volatile 解决的是多个线程中的可见性的问题

- synchronized 解决的是多个线程中的资源同步的问题