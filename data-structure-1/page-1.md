# Page 1

## DP

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        dp[0] = 1;
        int max = 1;
        for(int i=1; i<n; i++){
            dp[i] = 1;
            for(int j=0; j<i; j++){
                if(nums[i] > nums[j]){
                    dp[i] = Math.max(dp[i], dp[j]+1);
                }
                
            }
            max = Math.max(dp[i],max);
        }
        return max;
    }
}
```

$$
O(N^2)+O(N)
$$

## Greedy

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        List<Integer> res = new ArrayList<>();
        int n = nums.length;
        res.add(nums[0]);
        for(int i=1; i<n; i++){
            int lastIndex = res.size()-1;
            if(nums[i] > res.get(lastIndex)){
                res.add(nums[i]);
            }        
            else{
                int left=0, right=res.size()-1;
                while(left <= right){
                    int mid = (left+right)/2;
                    if(res.get(mid) < nums[i]){
                        left = mid+1;
                    }
                    else{
                        right = mid-1;
                    }
                }
                res.set(left,nums[i]);
            }
        }
        return res.size();
    }
}
```

$$
O(N*logN)+O(N)
$$

​

