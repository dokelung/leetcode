## solution

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        map = {}
        for i in range(len(nums)):
            c = target-nums[i]
            if c in map:
                return [map[c], i]
            map[nums[i]] = i
```

(python) 94.71%

## key

使用 hash table 以空間換取時間, hash table 搜尋時間近似 `O(1)`

## note

[Editorial Solution](https://leetcode.com/articles/two-sum/)
