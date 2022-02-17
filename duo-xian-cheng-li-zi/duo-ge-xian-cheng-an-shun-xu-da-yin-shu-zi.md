# 多个线程按顺序打印数字

```java
package com.company;
import java.util.*;
import java.util.Map.Entry;


public class Main{
    public static void main(String[] args) throws Exception
    {
        Thread t1 = new BaseImplement(0);
        Thread t2 = new BaseImplement(1);
        Thread t3 = new BaseImplement(2);
        t1.setName("t-0");
        t2.setName("t-1");
        t3.setName("t-2");
        t1.start();
        t2.start();
        t3.start();
    }
}
class BaseImplement extends Thread{
    // 统计次数
    private static int counter = 0;
    // 加锁
    private static Object lock = new Object();


    // 成员变量
    private int flag;
    private String value;

    // 构造方法
    public BaseImplement(int flag){
        this.flag = flag;
        this.value = value;
    }

    @Override
    public void run(){
        synchronized (lock){
            while(counter < 98){
                while(counter % 3 != flag){
                    try {
                        lock.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                System.out.println(Thread.currentThread().getName() + " " + counter);
                counter++;
                lock.notifyAll();
            }
        }

    }

}
```
