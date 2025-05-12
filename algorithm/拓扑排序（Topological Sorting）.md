```python
class Solution:  
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:  
        # 尝试在不具备图的基础知识的情况下来做这题  
  
        # 本题的核心点在于处理任意一个课程的时候，都需要考虑它是否有前置课程没有完成  
        # 只有说当前这个课程没有前置课程才能去处理它  
  
        # 1、记录每一个课程的情况  
        # 即，记录课程号与课程前置课程数量  
        # 使用哈希表来记录，可以快速获取和新增结果  
        # 在图这种数据结构里面专业术语叫做记录每个课程的【入度】  
        # key: 课号  
        # value: 学习这门课程的前置课程数量  
         
  
        # 2、初始化哈希表  
        inDegree = [0] * numCourses  
  
        # 4、记录每个课程之间的依赖关系  
        # 从而知道完成某个课程的时候，其它哪些课程被影响到了  
        # 由于被影响的课程可能有很多个，所以采用数组的形式保存被影响的那些课程  
        # 依赖关系，在图这种数据结构里面专业术语叫做邻接表  
        # key: 课号  
        # value: 依赖这门课的后续课，涉及多门，数组保存  
        map = defaultdict(list)  
  
        # 5、遍历 prerequisites 数组  
        # 更新 inDegree 与 map  
        for arr in prerequisites:  
  
            # prerequisites 数组中的每一个元素都是数组的形式  
            # 每一个元素记录了两个数据  
            # [first , second ]  
            # 学 first 的前置课程之一是完成 second  
            # 完成 second 会影响 first 的前置课程数量  
            first = arr[0]  
  
            second = arr[1]  
  
  
            # 6、更新入度  
            # 即更新 first 的前置课程数量，加 1 操作   
            inDegree[first] += 1  
  
            # 7、更新依赖  
            # 即记录 second 会影响哪些课程  
            # 此时 ， second 必然会影响 first  
            if map.get(second) is None:  
                map[second] = []  
                # print(map[second])  
  
            map[second].append(first)  
              
             
          
        # 9、开始去选修课程，只有没有前置课程的课程才能去选修  
        # 即入度为 0 的课程才能去选修  
        # 完成了一个入度为 0 的课程之后，会影响它的后续课，如果后续课为 0 了，又能选修了  
        # 以此类推  
        # 一开始把所有入度为 0 的课程都加入到队列里面  
        q = deque()  
  
        for i in range(len(inDegree)):  
            if inDegree[i] == 0:  
                q.append(i)  
              
        # 10、每个课程依次出列进行处理  
        # a、减小相关课的入度  
        # b、如果相关课的入度变为 0，也可以加入到队列里面  
        # 直到队列为空，即没有课程可以选修为止  
        while q:  
              
            # 课程出队  
            course = q.popleft()  
            # print(course)  
  
            # 如果发现该课程不会对任何一个课程有影响  
            # 即，如果发现依赖关系（邻接表）没有 course  
            # 那么直接去查看下一个课程的情况  
            if map.get(course) == None :  
                continue  
              
            # 否则开始更新当前课程的所有后续课程的【入度】情况  
            # 获取当前课程的所有的后续课程  
            successorList  = map.get(course)  
  
            # 更新后续课程的【入度】情况  
            for k in  successorList :  
  
                # 当前课程 course 选修完毕之后  
                # 每个后续课程的前置课程数量减一  
                # 即【入度】减一  
      
                inDegree[k] -= 1  
  
                # 如果发现后续某个课程【入度】为零  
                if inDegree[k] == 0 :   
                    # 把它也加入到队列处理  
                    q.append(k)  
        # 11、由于只有入度为零的课程才能被选修  
        # 因此，遍历 inDegree，查看是否还有入度为非零的课程  
        for key in inDegree :    
            # 如果有，说明当前课程无法被选修  
            if key != 0 :  
                # 即无法完成所有课程的学习  
                returnFalse  
              
        # 12、否则说明可以完成所有课程的学习  
        returnTrue
```

>**排序混乱，永远到不了终点。**
>**排序对了，一步步踏上去，就能到达目的地**
