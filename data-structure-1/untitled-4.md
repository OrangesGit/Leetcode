# 376. Wiggle Subsequence

## Greedy

```java
public class Solution {
    public int wiggleMaxLength(int[] nums) {
        int n = nums.length;
        if(n < 2) return n;
        int prediff = nums[1] - nums[0];
        int ret = prediff != 0 ? 2 : 1;
        for(int i = 2; i < n; i++){
            int currDiff = nums[i] - nums[i-1];
            if(currDiff < 0 && prediff >= 0 || currDiff > 0 && prediff <= 0){
                prediff = currDiff;
                ret++;
            }
        }
        return ret;
    }
}

// Or use this way

class Solution {
    public int wiggleMaxLength(int[] nums) {
        int n = nums.length;
        if(n == 1) return 1;
        int preDiff = nums[1] - nums[0];
        int res = preDiff == 0 ? 1 : 2;
        for(int i = 2; i < n; i++){
            int currDiff = nums[i] - nums[i-1];
            if(preDiff <= 0 && currDiff > 0 || preDiff >= 0 && currDiff < 0){
                res += 1;
                preDiff = currDiff;
            }
        }
        return res;
    }
}
```

$$
O(N)+O(1)
$$



