# leetcode102-levelOrder


方法一：用queue来做

        def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

            res = []

            q = collections.deque()
            q.append(root)

            while q:
                qLen = len(q)
                level = []
                for i in range(qLen):
                    cur = q.popleft()
                    if cur:
                        level.append(cur.val)
                        q.append(cur.left)
                        q.append(cur.right)
                        print(level)

                if level:
                    res.append(level)

            return res
