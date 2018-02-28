### 1.停止一个线程

- 1、~~~stop、suspend(resume)~~~

- 2、flag标志变量停止

- 3、通过interrupt来停止

### interrupt 停止不了的线程

```JAVA
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