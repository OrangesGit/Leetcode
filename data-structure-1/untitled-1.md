# Untitled

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> seen = new HashSet<>();
        for(int i : nums1){
            seen.add(i);
        }
        HashSet<Integer> inter = new HashSet<>();
        for(int i : nums2){
            if(seen.contains(i)){
                inter.add(i);
            }
        }
        int[] res = new int[inter.size()];
        int index = 0;
        for(int i : inter){
            res[index++] = i;
        }
        return res;
    }
}
```

$$
O(M+N)+O(M+N)
$$

