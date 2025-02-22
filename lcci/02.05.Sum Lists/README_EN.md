# [02.05. Sum Lists](https://leetcode-cn.com/problems/sum-lists-lcci)

[中文文档](/lcci/02.05.Sum%20Lists/README.md)

## Description

<p>You have two numbers represented by a linked list, where each node contains a single digit. The digits are stored in reverse order, such that the 1&#39;s digit is at the head of the list. Write a function that adds the two numbers and returns the sum as a linked list.</p>

<p>&nbsp;</p>

<p><strong>Example: </strong></p>

<pre>

<strong>Input: </strong>(7 -&gt; 1 -&gt; 6) + (5 -&gt; 9 -&gt; 2). That is, 617 + 295.

<strong>Output: </strong>2 -&gt; 1 -&gt; 9. That is, 912.

</pre>

<p><strong>Follow Up:&nbsp;</strong>Suppose the digits are stored in forward order. Repeat the above problem.</p>

<p><strong>Example: </strong></p>

<pre>

<strong>Input: </strong>(6 -&gt; 1 -&gt; 7) + (2 -&gt; 9 -&gt; 5). That is, 617 + 295.

<strong>Output: </strong>9 -&gt; 1 -&gt; 2. That is, 912.

</pre>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = cur = ListNode(0)
        carry = 0
        while l1 or l2 or carry:
            carry += (0 if not l1 else l1.val) + (0 if not l2 else l2.val)
            cur.next = ListNode(carry % 10)
            cur = cur.next
            carry //= 10
            l1 = None if not l1 else l1.next
            l2 = None if not l2 else l2.next
        return dummy.next
```

### **Java**

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
        while (l1 != null || l2 != null || carry != 0) {
            int s =
                (l1 == null ? 0 : l1.val) + (l2 == null ? 0 : l2.val) + carry;
            carry = s / 10;
            cur.next = new ListNode(s % 10);
            cur = cur.next;
            l1 = l1 == null ? null : l1.next;
            l2 = l2 == null ? null : l2.next;
        }
        return dummy.next;
    }
}
```

### **C++**

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode(0);
        ListNode* cur = dummy;
        int carry = 0;
        while (l1 || l2 || carry)
        {
            carry += (!l1 ? 0 : l1-> val) + (!l2 ? 0 : l2->val);
            cur->next = new ListNode(carry % 10);
            cur = cur->next;
            carry /= 10;
            l1 = l1 ? l1->next : l1;
            l2 = l2 ? l2->next : l2;
        }
        return dummy->next;
    }
};
```

### **JavaScript**

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function (l1, l2) {
    let carry = 0;
    const dummy = new ListNode(0);
    let cur = dummy;
    while (l1 || l2 || carry) {
        carry += (l1?.val || 0) + (l2?.val || 0);
        cur.next = new ListNode(carry % 10);
        carry = Math.floor(carry / 10);
        cur = cur.next;
        l1 = l1?.next;
        l2 = l2?.next;
    }
    return dummy.next;
};
```

### **Go**

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	dummy := &ListNode{}
	cur := dummy
	carry := 0
	for l1 != nil || l2 != nil || carry > 0 {
		if l1 != nil {
			carry += l1.Val
			l1 = l1.Next
		}
		if l2 != nil {
			carry += l2.Val
			l2 = l2.Next
		}
		cur.Next = &ListNode{Val: carry % 10}
		cur = cur.Next
		carry /= 10
	}
	return dummy.Next
}
```

### **...**

```

```

<!-- tabs:end -->
