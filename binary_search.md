## 二分查找

### 前提  
1） 增长序列  
2） 数字唯一

### 思路
mid == target，返回mid  
mid < target, 则left = mid + 1  
mid > target, 则right = mid - 1  

#### 如果数字存在
1） 序列：left/mid/right，三个位置相同，且mid等于target，返回mid  
2） 序列：left, mid, right，三个位置相邻，mid正好等于target，返回mid  
3） 序列：left/mid, right，mid和left相等，且mid正好等于target，返回mid  
4） 序列：left/mid, right，mid和left相等，right正好等于target，left会加一，变成 left/mid/right的情况  

#### 如果数字不存在
1） target会在left/mid，right之间，但不存在，这时，left = mid + 1，再比较，还是没有找到，然后right = mid - 1，left > right，表示没有找到  
2） target大于最大值，搜索的最后情况：left/mid/right，三个值相等，但还是没有找到，于是left = mid + 1，left > right，查找失败  
3）  target小于最小值，情况类似上面的。  

#### 容易出错的地方
取mid的时候溢出，用 mid = left + (right - left) // 2 可以防止溢出  
要保证left，right能相互靠拢，避免操作后数值不变，变成死循环  
