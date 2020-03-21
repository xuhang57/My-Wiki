# Add Two Numbers

Question: [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    }
}
```

## Simulation

Using a "carry" variable to simulate the addition operation. Don't forget to check the "carry" at the end.

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode dummy = new ListNode(-1);
        ListNode cur = dummy;
        while (l1 != null || l2 != null) {
            int sum = 0;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            sum += carry;
            carry = sum / 10;
            cur.next = new ListNode(sum % 10);
            cur = cur.next;
        }
        if (carry == 1) {
            cur.next = new ListNode(1);
        }
        return dummy.next;
    }
}
```

*Time: O(Max(M, N)) where M and N are the lengths of l1 and l2*  
*Space: O(Max(M,N) + 1)*

Lucas  
03/17/2020
