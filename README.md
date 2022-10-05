# LeetCode-623.-Add-One-Row-to-Tree

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def addOneRow(self, root: Optional[TreeNode], val: int, depth: int) -> Optional[TreeNode]:
        def helper(node,d):
            if not node or d>=depth:
                return
            else:
                if d==depth-1:
                    temp1,temp2=node.left,node.right
                    node.left=TreeNode(val,left=temp1)
                    node.right=TreeNode(val,right=temp2)
                else:
                    helper(node.left,d+1)
                    helper(node.right,d+1)
        if depth==1:
            node=TreeNode(val,left=root)
            return node
        else:
            helper(root,1)
        return root
