# LCP 07. 传递信息

## DFS

```java
class Solution {
    int res, n, k;
    HashMap<Integer, ArrayList<Integer>> graph;
    public int numWays(int n, int[][] relation, int k) {
        this.res = 0;
        this.n = n;
        this.k = k;
        graph = new HashMap<>();

        for (int i = 0; i < n; i++) {
            graph.put(i, new ArrayList());
        }
        for(int[] rel:relation){
            graph.get(rel[0]).add(rel[1]);
        }
        dfs(0,0);
        return res;

    }

    public void dfs(int index, int steps){
        if(steps == k){
            if(index == n-1){
                this.res++;
            }
            return;
        }
        for(int neighbor:graph.get(index))
            dfs(neighbor, steps+1);
    }
}
```

## Queue

```java
class Solution {
    public int numWays(int n, int[][] relation, int k) {
        ArrayList<ArrayList<Integer>> graph = new ArrayList<>();
        for(int i=0; i<n; i++) graph.add(new ArrayList());
        for(int[] rel:relation)
            graph.get(rel[0]).add(rel[1]);
        Queue<Integer> queue = new LinkedList<>();
        queue.offer(0);
        int steps = 0;
        while(!queue.isEmpty() && steps<k){
            steps++;
            int size = queue.size();
            for(int i=0; i<size; i++){
                int currNode = queue.poll();
                for(int neighbor: graph.get(currNode)){
                    queue.offer(neighbor);
                }
            }
        }
        int res = 0;
        for(int i:queue){
            if(i == n-1) res++;
        }
        return res;
    }
}
```
