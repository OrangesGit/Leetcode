# Queue

## What is Queue?

FIFO\(First Input First Output\) Order

## Queue.class

```java
public class Queue <V>{
    private int maxSize;
    private int currentSize;
    private V[] array;
    private int front;
    private int back;

//    Constructor
    public Queue(int max_size){
        maxSize = max_size;
        currentSize = 0;
        array = (V[]) new Object[maxSize];
        front = 0;
        back = -1;
    }
//    Helper Functions
    public boolean isEmpty(){
        return currentSize == 0;
    }
    public boolean isFull(){
        return currentSize == maxSize;
    }
    public V top(){
        return array[front];
    }
    public void enqueue(V data){
        if(isFull()){
            return;
        }
        back = (back + 1) % maxSize;
        array[back] = data;
        currentSize++;
    }
    public V dequeue(){
        if(isEmpty()){
            return null;
        }
        V temp = array[front];
        front = (front + 1) % maxSize;
        currentSize--;
        return temp;
    }
}

```

## Main.class

```java
package com.company;

public class Main {

    public static void main(String[] args) {
	// write your code here
        Queue<Integer> queue = new Queue<Integer>(5);
        //equeue 2 4 6 8 10 at the end
        queue.enqueue(2);
        queue.enqueue(4);
        queue.enqueue(6);
        queue.enqueue(8);
        queue.enqueue(10);
        //dequeue 2 elements from the start
        queue.dequeue();
        queue.dequeue();
        //enqueue 12 and 14 at the end
        queue.enqueue(12);
        queue.enqueue(14);

        System.out.println("Queue:");
        while(!queue.isEmpty()){
            System.out.print(queue.dequeue()+" ");
        }
    }
}

```

