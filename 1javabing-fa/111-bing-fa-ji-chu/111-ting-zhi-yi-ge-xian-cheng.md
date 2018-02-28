### 1.停止一个线程

- 1、~~~stop、suspend(resume)~~~

- 2、flag标志变量停止

- 3、通过interrupt来停止

### 2.interrupt 停止不了的线程？

> 注意  interrupt 只能把当前线程置为中断的状态标识，并不能真正的停止一个线程，所以会导致下列的问题

```java
class ThreadStopTest extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if (i == 50){
                this.interrupt();
            }
            System.out.println(i);
        }
    }
}
```

这段代码会一直打印到99才终止，**this.interrupt();**看起并没有起作用，是的还差一段代码

```java
   if (this.isInterrupted()){
     break;// 只是跳出当前的for循环，如果for循环外面有代码依旧会被执行
     // 或者使用return; 停止一个线程
   }
```
### 3. interrupt 和isInterrupted的区别：
