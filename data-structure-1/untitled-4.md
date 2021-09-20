# Untitled

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
```

$$
O(N)+O(1)
$$

