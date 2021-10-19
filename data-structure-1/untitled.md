# 25. Reverse Nodes in k-Group \*\*\*

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
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode new_head = new ListNode(0, head);
        ListNode curr = new_head, prev = new_head;
        while(curr != null){
            int count = 0;
            ListNode rev_tail = curr.next;
            while(count < k && curr != null){
                count++;
                curr = curr.next;
            }
            if(curr == null) break;
            ListNode next_node = curr.next;
            ListNode rev_head = reverse(rev_tail,k);
            prev.next = rev_head;
            rev_tail.next = next_node;
            prev = rev_tail;
            curr = rev_tail;
        }
        return new_head.next;
    }
    public ListNode reverse(ListNode curr, int k){
        ListNode rev_head = null;
        while(k > 0){
            ListNode next_node = curr.next;
            curr.next = rev_head;
            rev_head = curr;
            curr = next_node;
            k--;
        }
        return rev_head;
    }
}
```

## Conclusion

1. Create a function used to reverse the linked list
2. Treverse the whole linked list, find the k nodes. At this time, **head** = head of k nodes, **ptr** = next node of k nodes
3. After reverse k nodes, update the **new\_head,** **ktail.next**, **ktail and head**
4. At last, make **ktail.next = head **to link the rest nodes

$$
O(N)+O(1)
$$
