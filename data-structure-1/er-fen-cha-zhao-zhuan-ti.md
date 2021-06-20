# 二分查找专题

经典二分查找

```java
public static int binarySearch(int[] nums,int target,int left, int right) {
        //这里需要注意，循环条件
        while (left <= right) {
            //这里需要注意，计算mid
            int mid = left + ((right - left) >> 1);
            if (nums[mid] == target) {
                return mid;
            }else if (nums[mid] < target) {
                //这里需要注意，移动左指针
                left  = mid + 1;
            }else if (nums[mid] > target) {
                //这里需要注意，移动右指针
                right = mid - 1;
            }
        }
        //没有找到该元素，返回 -1
        return -1;
    }
```

[教程](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/solution/yi-wen-dai-ni-gao-ding-er-fen-cha-zhao-j-ymwl/)

[34.Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

