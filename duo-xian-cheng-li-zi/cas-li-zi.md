# CAS例子

```java
package com.company;
import java.util.*;
import java.util.Map.Entry;
import java.util.concurrent.ThreadPoolExecutor;
import java.util.concurrent.atomic.AtomicInteger;


public class Main{
    static AtomicInteger num = new AtomicInteger(0);
    public static void main(String[] args) throws Exception
    {
        for(int i=0; i<3; i++){
            Thread t = new Thread(new Runnable() {
                @Override
                public void run() {
                    while (num.get() < 1000){
                        System.out.println("Thread name" + Thread.currentThread().getName() + " - " + num.incrementAndGet());
                    }
                }
            });
            t.start();
        }
    }
}
```
