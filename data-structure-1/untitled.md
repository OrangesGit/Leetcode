# 25. Reverse Nodes in k-Group

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head, int k){
        ListNode ptr = head, new_head = null;
        while(k > 0){
            ListNode next_node = ptr.next;
            ptr.next = new_head;
            new_head = ptr;
            ptr = next_node;
            k--;
        }
        return new_head;
    }
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode new_head = null, ktail = null, ptr = head;
        while(ptr != null){
            int count = 0;
            while(count < k && ptr != null){
                count++;
                ptr = ptr.next;
            }
            if(count == k){
                ListNode rev_head = this.reverseList(head,k);
                if(new_head == null) new_head = rev_head;
                if(ktail != null) ktail.next = rev_head;
                ktail = head;
                head = ptr;
            }
        }
        if(ktail != null) ktail.next = head;
        return new_head != null ? new_head : head;
    }
}
```

## Conclusion

1. Create a function used to reverse the linked list
2. Treverse the whole linked list, find the k nodes. At this time, **head** = head of k nodes, **ptr** = next node of k nodes
3. After reverse k nodes, update the **new\_head,** **ktail.next**, **ktail and head**
4. At last, make **ktail.next = head** to link the rest nodes

$$
O(N)+O(1)
$$

