# #234 Palindrome Linked List

```java
import java.util.*;

class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}

class Solution {
    public boolean solution(ListNode head) {

        if(head.next == null) return true;

        List<Integer> list = new ArrayList<>();

        while(head!=null) {
            list.add(head.val);
            head = head.next;
        }
        int j=0;
        for(int i=list.size()-1; i>=list.size()/2; i--) {
            if(list.get(i) != list.get(j++)) return false;
        }
        return true;
    }
}
```

```java
// TEST CODE

import org.junit.Assert;
import org.junit.Test;

class ListNodeTest {
    int val;
    ListNodeTest next;
    ListNodeTest() {}
    ListNodeTest(int val) { this.val = val; }
    ListNodeTest(int val, ListNodeTest next) { this.val = val; this.next = next; }
}

public class SolutionTest {

    @Test
    public void solutionTest() {
        Solution s = new Solution();

        ListNode l1 = new ListNode(1);
        l1.next = new ListNode(2);
        l1.next.next = new ListNode(2);
        l1.next.next.next = new ListNode(1);

        ListNode l2 = new ListNode(1);
        l2.next = new ListNode(2);

        ListNode l3 = new ListNode(1);
        l3.next = new ListNode(2);
        l3.next.next = new ListNode(3);
        l3.next.next.next = new ListNode(2);
        l3.next.next.next.next = new ListNode(1);

        ListNode l4 = new ListNode(1);
        l4.next = new ListNode(1);

        Assert.assertEquals(true, s.solution(l1));

        Assert.assertEquals(false, s.solution(l2));

        Assert.assertEquals(true, s.solution(l3));

        Assert.assertEquals(true, s.solution(l4));
    }
}
```