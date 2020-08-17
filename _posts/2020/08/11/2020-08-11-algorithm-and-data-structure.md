<<<<<<< HEAD
---
title:  "Top Algorithms and Data Structures"
# tags: [Python,DataStructure,Algorithm] 
=======

---
title:  "Top Algorithms and Data Structures"
# tags: [Python,DataStructure,Algorithm]
>>>>>>> d61b1d17da6a8713c17ad1092e450c8f9967e39f
---

## Linked list related:

### Time complexity
![time-complexity](https://i.stack.imgur.com/SpCcj.png)

### Inserting data at a particular position in the linked list
[HackerRank: Insert a node at a specific position in a linked list](https://www.hackerrank.com/challenges/insert-a-node-at-a-specific-position-in-a-linked-list/problem)

```py
def insertNodeAtPosition(head, data, position):
    index = 0
    cur = head
    while index < position - 1:
        index += 1
        cur = cur.next

    new_node = SinglyLinkedListNode(data)
    new_node.next = cur.next
    cur.next = new_node

    return head
```

### Inserting data in the linked list

[HackerRank: Insert a node at the head of a linked list](https://www.hackerrank.com/challenges/insert-a-node-at-the-head-of-a-linked-list/problem)

```py
# SinglyLinkedListNode:
#     int data
#     SinglyLinkedListNode next
#
#
def insertNodeAtHead(llist, data):
    new_node = SinglyLinkedListNode(data)
    new_node.next = llist
    return new_node
```

Thought: In




stantiate a new node and point it's next pointer to the new head.


### Print data in a linked list with reverse order 

[HackerRank: Print in Reverse](https://www.hackerrank.com/challenges/print-the-elements-of-a-linked-list-in-reverse/problem)

```py
def reversePrint(head):
    print_list = [head.data];
    cur = head
    while cur.next != None:
        cur = cur.next
        print_list.append(cur.data)
    for e in print_list[::-1]:
        print(e)
```
Thought : Could be print then reverse or reverse the linked list then print. Based on it's difficulty being easy. I don't really want to put in all the effort in reversing it first.
### Print data in the linked list

[HackerRank: Print the elements of a linked list](https://www.hackerrank.com/challenges/print-the-elements-of-a-linked-list/problem)


```py
def printLinkedList(head):
    cur = head
    while cur !=None:
        print(cur.data)
        if cur.next == None:
            return
        cur = cur.next
```


### Reverse a linked list

[HackerRank: Reverse a linked list](https://www.hackerrank.com/challenges/reverse-a-linked-list/problem?h_r=internal-search)

```py
def reverse(head):
    cur = head
    last_node = None
    while True:
        next_node = cur.next
        cur.next = last_node
        if next_node == None:
            return cur
        last_node = cur
        cur = next_node
```

Thought: temporarily stores the previous node once assign the next node to another temporarily variable, point current pointer's next node back to the previous node.

## Binary search tree related:

tree is just special graph
Tree is not linear.
Traversal -> breadth-first and depth-first search



### Invert binary tree:
[LeetCode 226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/submissions/)

```py
class Solution(object):
    def invertTree(self, root):
        if root != None:
            if root.left !=None:
                self.invertTree(root.left)
            if root.right != None:
                self.invertTree(root.right)

            temp = root.left;
            root.left = root.right;
            root.right = temp;
        
            return root;
```

### Same Tree:
[LeetCode 100. Same Tree](https://leetcode.com/problems/same-tree/)

```py
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if p == None and q == None:
            return True;
        elif p != None and q != None:
            return p.val == q.val and self.isSameTree(p.left,q.left) and self.isSameTree(q.right,p.right)
        else:
            return False;
```

### Symmetry binary tree:
[LeetCode 101. Symmetric Tree](https://leetcode.com/problems/invert-binary-tree/submissions/)

```py
 def isSymmetric(self, root: TreeNode) -> bool:
        if root == None:
            return True
        
        def isMirrorTree(leftTree,rightTree):
            if leftTree != None and rightTree != None:
                return isMirrorTree(leftTree.left,rightTree.right) and isMirrorTree(leftTree.right,rightTree.left) and leftTree.val == rightTree.val

            elif leftTree == None and rightTree == None:
                return True
            else:
                return False;
        return isMirrorTree(root.left,root.right)
 
```
### Checking value of a binary tree:
[LeetCode 965. Univalued Binary Tree](https://leetcode.com/problems/univalued-binary-tree/)

```py
class Solution:
    def isUnivalTree(self, root: TreeNode) -> bool:
        # end node reached
        if root.left  == None and root.right == None:
            return True

        # only exist one node 
        elif root.left != None and root.right == None:
            return root.left.val == root.val and self.isUnivalTree(root.left)
        elif root.right != None and root.left == None:
            return root.right.val == root.val and self.isUnivalTree(root.right)
        else:
            # both node exist
            return root.val == root.right.val and root.val == root.left.val and self.isUnivalTree(root.left) and self.isUnivalTree(root.right)
```
### Breadth-first (level order):
visiting children before visiting grand children

FIFO queue
```py


```

### Depth-first 
visiting a complete sub-tree :
Pre-order (DLR)
In-order (LDR)
Post-order (LRD)