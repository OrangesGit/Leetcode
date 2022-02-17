# 多个线程循环打印ABC

```java
package com.company;
import java.util.*;
import java.util.Map.Entry;


public class Main{
    public static void main(String[] args) throws Exception
    {
        Thread t1 = new BaseImplement(0, "A");
        Thread t2 = new BaseImplement(1, "B");
        Thread t3 = new BaseImplement(2, "C");
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
    public BaseImplement(int flag, String value){
        this.flag = flag;
        this.value = value;
    }

    @Override
    public void run(){
        synchronized (lock){
            for(int i=0; i<10; i++){
                while(counter % 3 != flag){
                    try {
                        lock.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                System.out.println(Thread.currentThread().getName() + " - " + this.value);
                counter++;
                lock.notifyAll();
            }
        }

    }

}
```
