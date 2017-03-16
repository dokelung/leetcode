## solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        dummy_head = ListNode(0)
        node = dummy_head
        node1 = l1
        node2 = l2
        carry = 0
        
        while node1 or node2:
            v = (node1.val if node1 else 0) + (node2.val if node2 else 0) + carry
            carry = 0
            if v >= 10:
                carry = 1
                v -= 10
            node.next = ListNode(v)
            # ---
            if node1:
                node1 = node1.next
            if node2:
                node2 = node2.next
            node = node.next
        if carry > 0:
            node.next = ListNode(carry)
            
        return dummy_head.next
```

(python) 94.75%

## key

1. 使用 `dummy_head` 統一全部的行為(不要特別處理第一個 node)
2. 最後一個 `carry` 有值的狀況出了迴圈再處理, 不要在 `while` 的判斷式中判斷 `carry` 有無值
3. `node1` 與 `node2` 只有在其 `next` 有值的時候再更新, 因為 `None` 的 `next` 還會是 `None`, 不必更新

## note

[Editorial Solution](https://leetcode.com/articles/add-two-numbers/)

可能要研究一下使用加減法比較快還是除法或取餘比較快
