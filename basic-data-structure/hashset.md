# HashSet

```java
class Bucket{
    private LinkedList<Integer> container;
    public Bucket(){
        container = new LinkedList<>();
    }
    public void insert(Integer val){
        int index = container.indexOf(val);
        if(index == -1){
            container.addFirst(val);
        }
    }
    public void delete(Integer val){
        container.remove(val);
    }
    public boolean exists(Integer val){
        return -1 != container.indexOf(val);
    }
}
class MyHashSet {
    private Bucket[] bucketArray;
    private final int base;
    /** Initialize your data structure here. */
    public MyHashSet() {
        base = 857;
        bucketArray = new Bucket[base];
        for(int i = 0; i < base; i++) bucketArray[i] = new Bucket();
    }
    public int _hash(int key){
        return key % base;
    }
    
    public void add(int key) {
        int index = _hash(key);
        bucketArray[index].insert(key);
    }
    
    public void remove(int key) {
        int index = _hash(key);
        bucketArray[index].delete(key);
    }
    
    /** Returns true if this set contains the specified element */
    public boolean contains(int key) {
        int index = _hash(key);
        return bucketArray[index].exists(key);

    }
}

/**
 * Your MyHashSet object will be instantiated and called as such:
 * MyHashSet obj = new MyHashSet();
 * obj.add(key);
 * obj.remove(key);
 * boolean param_3 = obj.contains(key);
 */
```

