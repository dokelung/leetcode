## solution

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        map = {}
        max_length = front = back = 0
        while front < len(s):
            if s[front] in map:
                max_length = max(max_length, front-back)
                while back < map[s[front]]:
                    del map[s[back]]
                    back += 1
                back += 1
            map[s[front]] = front
            front += 1
        max_length = max(max_length, front-back)
        return max_length
```

(python) 86.32%

## key

* 使用 sliding window
* 使用 `set` 或 `mapping`, 記得保持更新

## note

[Editorial Solution](https://leetcode.com/articles/longest-substring-without-repeating-characters/)
