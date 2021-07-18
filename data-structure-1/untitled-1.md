# Untitled

```java
class Solution {
    public String simplifyPath(String path) {
        Stack<String> stack = new Stack<>();
        String[] components = path.split("/");
        for(String directory : components){
            if(directory.equals(".") || directory.isEmpty()){
                continue;
            }
            else if(directory.equals("..")){
                if(!stack.isEmpty()){
                    stack.pop();
                }
                
            }
            else{
                stack.push(directory);
            }
        }
        StringBuilder result = new StringBuilder();
        for(String dir : stack){
            result.append("/");
            result.append(dir);
        }
        return result.length() > 0 ? result.toString() : "/";
    }
}
```

$$
O(N)+O(N)
$$

## Conclusion

1.首先用split函数将字符串分割

2.遍历每一个分割出的字符串并根据情况决定是否将该字符串push进stack中

3.将stack内的结果组合成最终的结果

