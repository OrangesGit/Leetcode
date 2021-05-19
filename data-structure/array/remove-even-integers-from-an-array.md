# 1. Remove Even Integers from an Array

```java
class CheckRemoveEven {

	public static int[] removeEven(int[] arr) {
		int oddNum = 0;
		for(int i = 0; i < arr.length; i++){
			if(arr[i] % 2 != 0) oddNum++;
		}
		int[] result = new int[oddNum];

		int oddEnd = 0;
		for(int i = 0; i < arr.length; i++){
			if(arr[i] % 2 != 0) result[oddEnd++] = arr[i];
		}
		// Write - Your - Code- Here
		return result; // change this and return the correct result array
	}
}
```

## 总结

1. 遍历一遍数组确定有几个偶数
2. 创建一个数组存储偶数
3. 将满足条件的数字放入创建的数组



