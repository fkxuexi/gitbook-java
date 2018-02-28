### 1.停止一个线程

- 1、~~~stop、suspend(resume)~~~

- 2、flag标志变量停止

- 3、通过interrupt来停止

### 2.interrupt 停止不了的线程

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
     break;
   }
```

是的，现在线程停了下来，你看到了你想要的结果，打印到50 便停止了

> this.interrupt() 测试当前线程有没有中断，执行后将线程的状态标识置为与当前相反的状态，第一次调用为true，第二次调用则为false，

> this.isInterrupted() 只检测线程的从动态，并不清除线程的状态


### 3.线程真的停止了吗
