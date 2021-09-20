# 122. Best Time to Buy and Sell Stock II

## Greedy

```java
class Solution {
    public int maxProfit(int[] prices) {
        int max = 0, res = 0;
        for(int i = 1; i < prices.length; i++){
            max = Math.max(0, prices[i] - prices[i-1]);
            if(max > 0)
                res += max;
        }
        return res;
    }
}
```

$$
O(N)+O(1)
$$

