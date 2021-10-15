# Queue

## Implement Queue(Leetcode 622)

```java
class MyCircularQueue {
    private int[] array;
    private int head;
    private int tail;
    private int size;
    public MyCircularQueue(int k) {
        array = new int[k];
        head = -1;
        tail = -1;
        size = k;
    }
    
    public boolean enQueue(int value) {
        if(isFull()){
            return false;
        }
        if(isEmpty()){
            head = 0;
        }
        tail = (tail + 1) % size;
        array[tail] = value;
        return true;
    }
    
    public boolean deQueue() {
        if(isEmpty()){
            return false;
        }
        if(head == tail){
            head = -1;
            tail = -1;
            return true;
        }
        head = (head + 1) % size;
        return true;
    }
    
    public int Front() {
        if(isEmpty()){
            return - 1;
        }
        return array[head];
    }
    
    public int Rear() {
        if(isEmpty()){
            return -1;
        }
        return array[tail];
    }
    
    public boolean isEmpty() {
        return head == -1;
    }
    
    public boolean isFull() {
        return (tail + 1) % size == head;
    }
}

/**
 * Your MyCircularQueue object will be instantiated and called as such:
 * MyCircularQueue obj = new MyCircularQueue(k);
 * boolean param_1 = obj.enQueue(value);
 * boolean param_2 = obj.deQueue();
 * int param_3 = obj.Front();
 * int param_4 = obj.Rear();
 * boolean param_5 = obj.isEmpty();
 * boolean param_6 = obj.isFull();
 */
```

## Notes

在Java中，并没有 enqueue 和 dequeue，有的是如下操作

[Official Introduction](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#add\(E\))

| _Methods_   | _Throws exception_                                                                        | _Returns special value_                                                                 |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| **Insert**  | [`add(e)`](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#add\(E\))       | [`offer(e)`](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#offer\(E\)) |
| **Remove**  | [`remove()`](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#remove\(\))   | [`poll()`](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#poll\(\))     |
| **Examine** | [`element()`](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#element\(\)) | [`peek()`](https://docs.oracle.com/javase/7/docs/api/java/util/Queue.html#peek\(\))     |

