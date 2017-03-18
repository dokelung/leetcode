## solution

```python
class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        nums = nums2[:]
        s= 0
        for i in nums1:
            e = len(nums)-1
            while s <= e:
                m = (s+e)/2
                if i >= nums[m]:
                    s = m+1
                elif i < nums[m]:
                    e = m-1
            nums.insert(s, i)
        if len(nums)%2 == 0:
            return (nums[len(nums)/2] + nums[len(nums)/2-1])/2.0
        else:
            return nums[len(nums)/2]
```

(python) 35.22%

## key

## note
