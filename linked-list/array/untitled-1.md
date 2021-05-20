# 10. Rearrange Sorted Array in Max/Min Form

## Problem Statement

In this problem, you have to implement the `void maxMin(int[] arr)` method. This will re-arrange the elements of a sorted array in such a way that the first position will have the largest number, the second will have the smallest, the third will have the second-largest, and so on.

```java
class CheckMaxMin {

  public static void maxMin(int[] arr) {

    // Write - Your - Code
    int len = arr.length, left = 0, right = arr.length - 1, start = 0;
    int[] result = new int[len];
    while(left < right){
      result[start++] = arr[right--];
      result[start++] = arr[left++];
      if(left == right) result[start++] = arr[left];
    }
    for(int i = 0; i < arr.length; i++){
      arr[i] = result[i];
    }
  }
}
```

## Conclusion

1. Create a array, of which length is as same as the arr
2. Put the elements in order according to the problem statement \(2 conditions: Even and Odd situations\)



