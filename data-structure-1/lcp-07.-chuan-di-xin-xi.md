# LCP 07. 传递信息

## Queue

```java
class Solution {
    public int numWays(int n, int[][] relation, int k) {
        Queue<Integer> queue = new LinkedList<>();
        ArrayList<Integer>[] adj = new ArrayList[n];
        for(int i=0; i<n; i++) adj[i] = new ArrayList<>();
        for(int[] currRel : relation){
            int head = currRel[0];
            int succ = currRel[1];
            adj[head].add(succ);
        }
        int steps = 0;
        queue.offer(0);
        while(!queue.isEmpty() && steps<k){
            steps++;
            int size = queue.size();
            for(int i=0; i<size; i++){
                int head = queue.poll();
                for(int j : adj[head]){
                    queue.offer(j);
                }
            }
        }

        int ways = 0;
        while(!queue.isEmpty()){
            if(queue.poll() == n-1)
                ways++;
        }
        return ways;
        
    }
}
```
