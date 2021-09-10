# 剑指 Offer 05. 替换空格 LCOF

```java
class Solution {
    public String replaceSpace(String s) {
        if(s == null) return null;
        StringBuilder str = new StringBuilder();
        for(int i = 0; i < s.length(); i++){
            if(" ".equals(String.valueOf(s.charAt(i)))){
                str.append("%20");
            }
            else{
                str.append(String.valueOf(s.charAt(i)));
            }
        }
        return str.toString();
    }
}
```

$$
O(N)+O(N)
$$

