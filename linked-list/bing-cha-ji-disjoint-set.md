# 并查集(Disjoint Set)

[教程](https://www.techiedelight.com/disjoint-set-data-structure-union-find-algorithm/)

此代码没有定义constructor，而是通过makeSet方法指定，两者都行。

## 基本构造

主要包含两个方法：

1.  Find(int child)

    &#x20;用来找到当前child的parent是谁
2.  Union(int child, int parent)

    将child和parent合并

同时需要一个数据类型记录他们的关系

## HashMap实现

可以选HashMap，通过get方法找到父亲是谁

```java
package com.company;

import java.util.HashMap;

public class DJS {
    private HashMap<Integer, Integer> parent = new HashMap<>();
    public DJS(int[] inputs){
        for(int i:inputs)
            parent.put(i,i);
    }
    public int Find(int curr){
        if(parent.get(curr) == curr) return curr;
        return Find(parent.get(curr));
    }
    public void Union(int ch, int pa){
        int x = parent.get(ch);
        int y = parent.get(pa);
        parent.put(x, y);
    }
}

```

```java
package com.company;
import java.util.*;

public class Main{
    public static void printSets(int[] universe, DisjointSet ds)
    {
        for (int i: universe) {
            System.out.print(ds.Find(i) + " ");
        }

        System.out.println();
    }

    public static void printSetsDJS(int[] universe, DJS ds)
    {
        for (int i: universe) {
            System.out.print(ds.Find(i) + " ");
        }

        System.out.println();
    }

    // Disjoint–Set data structure (Union–Find algorithm)
    public static void main(String[] args)
    {
        // DJS
        int[] inputs = {1, 2, 3, 4, 5};
        DJS djs = new DJS(inputs);
        printSetsDJS(inputs, djs);
        djs.Union(4,3);
        printSetsDJS(inputs, djs);
        djs.Union(2,1);
        printSetsDJS(inputs, djs);
        djs.Union(1,3);
        printSetsDJS(inputs, djs);

    }
}
```

## int\[] 实现

```java
package com.company;

import java.util.HashMap;

public class DJS {
    private int[] parent;
    public DJS(int dummy){
        parent = new int[dummy+1];
        for(int i=0; i<=dummy; i++){
            parent[i] = i;
        }
    }
    public int FIND(int currNode){
        while (currNode != parent[currNode]) {
            parent[currNode] = parent[parent[currNode]];
            currNode = parent[currNode];
        }
        return currNode;
    }
    public void UNION(int a, int b){
        int x = FIND(a);
        int y = FIND(b);
        if(x != y) parent[x] = y;
    }
    public void printSets(int dummy){
        for(int i=0; i<=dummy; i++){
            System.out.println(i + "-" +parent[i]);
        }
    }
}

```
