#### 1、synchronized

- 1、一个线程访问一个对象的synchronized(this)，其他访问该对象的的synchronized将被阻塞

- 2、当一个线程访问一个对象的synchronized(this)时，其他方法仍可以放非synchronized方法

- 3、当synchronized 修饰静态方法是，静态方法是属于类的，因为所有此类的实例将共享同一把锁，即两个不同的对象并发执行时依然要执行同步

- 4、当synchronized修饰类是同修饰静态方法一致