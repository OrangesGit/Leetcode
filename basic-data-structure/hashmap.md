# HashMap

```java
class Pair<U, V>{
    public U key;
    public V val;
    public Pair(U key, V val){
        this.key = key;
        this.val = val;
    }
}
class Bucket{
    public List<Pair<Integer, Integer>> container;
    public Bucket(){
        this.container = new LinkedList<>();
    }
    public Integer get(Integer key){
        for(Pair<Integer, Integer> pair : container){
            if(pair.key.equals(key)){
                return pair.val;
            }
        }
        return -1;
    }
    public void update(Integer key, Integer val){
        boolean found = false;
        for(Pair<Integer, Integer> pair : container){
            if(pair.key.equals(key)){
                pair.val = val;
                found = true;
                break;
            }
        }
        if(!found){
            container.add(new Pair<Integer, Integer>(key, val));
        }
    }
    public void remove(Integer key){
        for(Pair<Integer, Integer> pair : container){
            if(pair.key.equals(key)){
                container.remove(pair);
                break;
            }
        }
    }
}
class MyHashMap {
    public List<Bucket> hash_map;
    public final int base;

    /** Initialize your data structure here. */
    public MyHashMap() {
        base = 857;
        hash_map = new ArrayList<>();
        for(int i = 0; i < base; i++) 
            hash_map.add(new Bucket());
    }
    
    /** value will always be non-negative. */
    public void put(int key, int value) {
        int hash_index = key % base;
        this.hash_map.get(hash_index).update(key, value);
    }
    
    /** Returns the value to which the specified key is mapped, or -1 if this map contains no mapping for the key */
    public int get(int key) {
        int hash_index = key % base;
        return this.hash_map.get(hash_index).get(key);
    }
    
    /** Removes the mapping of the specified value key if this map contains a mapping for the key */
    public void remove(int key) {
        int hash_index = key % base;
        this.hash_map.get(hash_index).remove(key);
    }
}

/**
 * Your MyHashMap object will be instantiated and called as such:
 * MyHashMap obj = new MyHashMap();
 * obj.put(key,value);
 * int param_2 = obj.get(key);
 * obj.remove(key);
 */
```



