# #234 Palindrome Linked List

- 팰린드롬(palindrome)이란 우리 말로 '회문(回文)'으로 번역되며 'eye', 'civic'처럼 역순으로 읽어도 같은 말이나 구절 또는 숫자를 말한다.
- 주어진 ListNode가 회문이면 true를 반환하는 문제.

![234 Palindrome Linked List_1](https://user-images.githubusercontent.com/64471645/115528261-d970ab80-a2cc-11eb-97c7-96a195c158d8.JPG)
---

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
---
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

---
```java
// Before Refactoring

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
    public boolean isPalindrome(ListNode head) {
        
        if(head.next == null) return true;

        List<Integer> list = new ArrayList<>();
        List<Integer> inReverseList = new ArrayList<>();
        int headCnt = 0;

        while(head!=null) {
            list.add(head.val);
            head = head.next;
            headCnt++;
        }
        if(headCnt % 2 == 0) {
            for(int i=headCnt-1; i>=headCnt/2; i--) {
                inReverseList.add(list.get(i));
            }
        }
        else {
            for(int i=headCnt-1; i>headCnt/2; i--) {
                inReverseList.add(list.get(i));
            }
        }
        for(int i=0; i<headCnt/2; i++) {
            if(list.get(i) != inReverseList.get(i)) return false;
        }
        return true;        
    }
}
```
