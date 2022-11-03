# leetcode102-levelOrder


方法一：用queue来做
       引进queue的方式是 = collections.deque（）或者 deque

        def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

            res = []

            q = collections.deque()
            q.append(root)   

            while q:
                qLen = len(q)                   
                level = []
                for i in range(qLen):           //遍历每层的每个元素
                    cur = q.popleft()
                    if cur:
                        level.append(cur.val)
                        q.append(cur.left)      //下一层加进去
                        q.append(cur.right)
                        print(level)

                if level:
                    res.append(level)

            return res
  
  
 方法二：一样的更好理解
 
        解释：其实重点是： 1.每层值放在queue里
                        2.取出来放在level这个list里面
                        3.把所有的level放进res里面！
 
         def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

                        if not root:
                            return []
                        queue = deque([root])
                        res = []

                        while queue:
                            level = []
                            for i in range(len(queue)):          // queue里面的值
                                cur = queue.popleft()            // popleft（）取值
                                level.append(cur.val)            // 加到level这个list里面
                                if cur.left:
                                    queue.append(cur.left)       // queue里面装下一层的值，然后重复
                                if cur.right:
                                    queue.append(cur.right)
                            res.append(level)

                        return res      
            
  下一个解释，时间超了，但是好理解         
          
                        res = []
                        level = [root]

                        while root and level:
                            cur = []
                            nextLevel = []
                            for node in level:
                                cur.append([node.val])                  //第一层，加进去【】
                                if node.left:
                                    nextLevel.append(node.left)         //下一层加上左右支，下一层按第一层一样
                                if node.right:
                                    nextLevel.append(node.right)
                        res.append(cur)
                        level = nextLevel

                        return res
