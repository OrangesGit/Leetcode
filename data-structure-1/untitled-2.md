---
description: 622. 设计循环队列
---

# 622.Design Circular Queue

```java
class MyCircularQueue {
    private int head, tail, size;
    private int[] data;
    public MyCircularQueue(int k) {
        head = -1;
        tail = -1;
        size = k;
        data = new int[size];
    }
    
    public boolean enQueue(int value) {
        if(isFull()){
            return false;
        }
        if(isEmpty()){
            head = 0;
        }
        tail = (tail + 1) % size;
        data[tail] = value;
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
            return -1;
        }
        return data[head];

    }
    
    public int Rear() {
        if(isEmpty()){
            return -1;
        }
        return data[tail];
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

## Conclusion

基础题，设计一个基础的循环队列，30行要特别注意

$$
O(1)+(N)
$$



