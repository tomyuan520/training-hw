# 94.二叉树的中序遍历
[lc link](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

* 很标准的二叉树题目，根据规律因为所需要的是中序，所以就是左中右。
* 同理也可以得到前序和后序遍历，一个中左右，一个左右中。
* 这题递归会明白很多，其中用到了dfs的思想。
* 于8.15做了第一次。

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def dfs(r):
            if not r:
                return
            # 中序遍历，左 加值 右
            dfs(r.left)
            res.append(r.val)
            dfs(r.right)
        dfs(root)
        return res
```