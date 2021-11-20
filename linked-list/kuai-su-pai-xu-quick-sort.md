# 快速排序(Quick Sort)

```
import java.util.*;
public class Main{
    public static void main(String[] args){
        int[] nums =  {10, 80, 30, 90, 40, 50, 70};
        quickSort(nums, 0,6);
        for(int i:nums){
            System.out.println(i);
        }
    }
    public static void quickSort(int[] nums, int low, int high){
        if(low < high){
            int pi = partition(nums, low, high);
            quickSort(nums, low, pi-1);
            quickSort(nums, pi+1,  high);
        }
    }
    public static int partition(int[] nums, int low, int high){
        int i = low-1, pivot = nums[high];
        for(int j=low; j<high; j++){
            if(nums[j] < pivot){
                i++;
                swap(nums,i,j);
            }
        }
        swap(nums,i+1, high);
        return i+1;
    }

    public static void swap(int[] nums, int i, int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

$$
O(N*logN)+O(N)
$$
