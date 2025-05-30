
- **等概率洗牌算法**
每一步都维护了当前未处理区间的均匀概率；最终确保了每个排列的出现概率都是 1/n!

```python
import random  
  
def knuth_shuffle(arr):  
    n = len(arr)  
    for i in range(n - 1, 0, -1):  
        j = random.randint(0, i)  
        arr[i], arr[j] = arr[j], arr[i]
```

>有一种美，是“有限成本”内的“无限可能”。
>有时候，真正让你惊艳的，不是技术的厚重，而是思维的轻盈。


算法本质是从最后一个位置开始，每个位置随机发一张剩余的牌，所以每个位置放任何一张牌的概率都是均等的，这样就确保打乱后所有排列的概率均等。另外在原数组上交换元素而不是开辟新数组也属于基操了