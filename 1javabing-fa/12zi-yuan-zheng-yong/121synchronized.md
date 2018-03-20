#### 1、synchronized

- 1、一个线程访问一个对象的synchronized(this)，其他访问该对象的的synchronized将被阻塞

- 2、当一个线程访问一个对象的synchronized(this)时，其他方法仍可以放非synchronized方法