# Convert-Sorted-List-to-Binary-Search-Tree
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def sortedListToBST(self, head: ListNode | None) -> TreeNode | None:
        if head is None:
            return head
        r=[]
        temp=head
        while temp:
            r.append(temp.val)
            temp=temp.next
        def bst(left,right):
            if left>right:
                return None
            mid=(left+right)//2
            root=TreeNode(r[mid])
            root.left=bst(left,mid-1)
            root.right=bst(mid+1,right)
            return root
        return bst(0,len(r)-1)
