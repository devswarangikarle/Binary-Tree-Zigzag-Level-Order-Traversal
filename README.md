# Binary-Tree-Zigzag-Level-Order-Traversal

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

Constraints:
The number of nodes in the tree is in the range [0, 2000].
-100 <= Node.val <= 100

class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

        if not root:
            return []

        level = 0
        ans = []
        queue = deque()
        queue.append(root)

        while queue:
            curr_len = len(queue)
            curr_queue = deque()

            for i in range(curr_len):
                curr = queue.popleft()
                if level % 2 == 0:
                    curr_queue.append(curr.val)
                else:
                    curr_queue.appendleft(curr.val)
            
                if curr.left:
                    queue.append(curr.left)
                if curr.right:
                    queue.append(curr.right)
            
            ans.append(list(curr_queue))
            level += 1
                
        return ans
            

        

