# Stack



LIFO\(Last Input First Output\) Order

e.g.

1. Depth First Search
2. Expression Evaluation Algorithm

## Basic Structure

### Stack.class

```java
public class Stack <V> {
    private int top;
    private int maxSize;
    private V[] array;
//    Constructor
    public Stack(int max_size){
        this.top = -1;
        this.maxSize = max_size;
        this.array = (V[]) new Object[max_size];
    }
//    Some Helper Functions
    public boolean isEmpty(){
        return this.top == -1;
    }
    public boolean isFull(){
        return this.top == this.maxSize - 1;
    }
    public V top(){
        if(isEmpty()){
            return null;
        }
        return array[top];
    }
    public void push(V data){
        if(isFull()){
            System.err.println("Stack is full!");
        }
        array[++top] = data;
    }
    public V pop(){
        if(isEmpty()){
            return null;
        }
        return array[top--];
    }
}

```

### Main.class

```java
package com.company;


public class Main {

    public static void main(String[] args) {
	// write your code here
        Stack<Integer> stack = new Stack<Integer>(5);
        System.out.print("Elements pushed in the Stack: ");
        for (int i = 0; i < 5; i++) {
            stack.push(i); //pushes 5 elements (0-4 inclusive) to the stack
            System.out.print(i + " ");
        }
        System.out.println("\nIs Stack full? \n" + stack.isEmpty());
        System.out.print("Elements popped from the Stack: ");
        for (int i = 0; i < 5; i++) {
            System.out.print(stack.pop()+" "); //pops all 5 elements from the stack and prints them
        }
        System.out.println("\nIs Stack empty? \n" + stack.isEmpty());
    }
}

```

## Conclusion

Stack初始容量为10，当被填满的时候，会double容量

