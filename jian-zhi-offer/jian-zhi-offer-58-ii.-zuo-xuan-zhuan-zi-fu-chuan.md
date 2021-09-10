# 剑指 Offer 58 - II. 左旋转字符串

## Use Reverse

```java
class Solution {
    public String reverseLeftWords(String s, int n) {
        StringBuilder sb = new StringBuilder(s);
        reverse(sb, 0, n-1);
        reverse(sb, n, s.length() - 1);
        reverse(sb, 0, s.length() - 1);
        return sb.toString();
    }
    public void reverse(StringBuilder sb, int left, int right){
        while(left < right){
            char curr = sb.charAt(left);
            sb.setCharAt(left, sb.charAt(right));
            sb.setCharAt(right, curr);
            left++;
            right--;
        }
    }
}
```

$$
O(N)+O(N)
$$

## Use Slices

```java
class Solution {
    public String reverseLeftWords(String s, int n) {
        StringBuilder sb = new StringBuilder();
        for(int i = n; i < s.length(); i++){
            sb.append(s.charAt(i));
        }
        for(int i = 0; i < n; i++){
            sb.append(s.charAt(i));
        }
        return sb.toString();
    }
}
```

$$
O(N)+O(N)
$$

