# 253. Meeting Rooms II

## Chrological Order

```java
class Solution {
    public int minMeetingRooms(int[][] intervals) {
        int n = intervals.length;
        int[] start_time = new int[n];
        int[] end_time = new int[n];
        for(int i = 0; i < n;i++){
            start_time[i] = intervals[i][0];
            end_time[i] = intervals[i][1];
        }
        Arrays.sort(start_time);
        Arrays.sort(end_time);
        int used_room = 0;
        int start_ptr = 0, end_ptr = 0;
        while(start_ptr < n){
            if(start_time[start_ptr] >= end_time[end_ptr]){
                used_room -= 1;
                end_ptr++;
            }
            used_room++;
            start_ptr++;
        }
        return used_room;
    }
}
```

$$
O(N*logN)+O(1)
$$

```java
class Solution {
    public int minMeetingRooms(int[][] intervals) {
        PriorityQueue<Integer> endTime = new PriorityQueue<Integer>();
        // Queue<Integer> endTime = new LinkedList<>();
        Arrays.sort(intervals, (a,b) -> {return a[0]- b[0];
        });
        endTime.add(intervals[0][1]);
        for(int i = 1; i < intervals.length; i++){
            if(intervals[i][0] >= endTime.peek()){
                endTime.remove();
            }
            endTime.add(intervals[i][1]);
        }
        return endTime.size();

    }
}
```

$$
O(N*logN)+O(N)
$$
