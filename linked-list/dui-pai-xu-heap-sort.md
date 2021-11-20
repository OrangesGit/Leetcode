# 堆排序(Heap Sort)

```java
import java.util.*;public class Main{
    public static void main(String[] args){
        int[] nums = {10, 80, 30, 90, 40, 50, 70};

        heapSort(nums);
//        heapifyTest(nums, 7, 0);
        for(int i:nums){
            System.out.println(i);
        }
    }

    public static void heapify(int[] nums, int n, int root){
        int left = 2*root + 1;
        int right = 2*root + 2;
        int largest = root;
        if(left < n && nums[left] > nums[largest]) largest = left;
        if(right < n && nums[right] > nums[largest]) largest = right;

        if(largest != root){
            int temp = nums[root];
            nums[root] = nums[largest];
            nums[largest] = temp;

            heapify(nums, n, largest);
        }
    }

    public static void heapSort(int[] nums){
        int n=nums.length;
        for(int i=n/2-1; i>=0; i--){
            heapify(nums,n,i);
        }

        for(int i=n-1; i>0; i--){
            int temp = nums[0];
            nums[0] = nums[i];
            nums[i] = temp;
            heapify(nums, i, 0);
        }
    }


}
```

$$
O(N*logN)+O(1)
$$
