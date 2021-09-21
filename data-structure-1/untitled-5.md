# 45. Jump Game II

## Greedy

```java
class Solution {
    public int jump(int[] nums) {
        int farthest = 0, steps = 0, currentJumpEnd = 0;
        for(int i = 0; i < nums.length - 1; i++){
            farthest = Math.max(farthest, nums[i] + i);
            if(i == currentJumpEnd){
                steps++;
                currentJumpEnd = farthest;
            }
        }
        return steps;
    }
}
```

$$
O(N)+O(1)
$$

