# 二分查找变种

找到第一个比目标元素大的下标

```java
public static int getPos(int[] nums, int target){
        int left = 0,right = nums.length - 1;
        int pos = -1;
        while(left <= right){
            int mid = left + ((right - left)>>1);
            if(nums[mid] > target) {
                if(mid == 0 || nums[mid - 1] <= target){
                    return mid;
                }
                else{
                    right = mid - 1;
                }
            }
            else if(nums[mid] <= target){
                left = mid + 1;
            }
        }
        return pos;
    }
```

找到最后一个小于目标元素的索引

```java
public static int getPos(int[] nums, int target){
        int left = 0,right = nums.length - 1;
        int pos = -1;
        while(left <= right){
            int mid = left + ((right - left) >> 1);
            if(nums[mid] < target){
                if(mid == nums.length - 1 || nums[mid + 1] >= target){
                    return mid;
                }
                else{
                    left = mid + 1;
                }
            }
            else if(nums[mid] >= target){
                right = mid - 1;
            }
        }
        return pos;
    }
```

