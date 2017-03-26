## solution

```python
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        b = 0
        e = 0
        for i in range(len(s)):
            eve_stop = odd_stop = False
            for j in range(1, 502):
                if not eve_stop:
                    eve_stop = (i+j >= len(s) or i-j+1 < 0) or s[i+j]!=s[i-j+1]
                    if eve_stop:
                        if 2*j-2 > e-b:
                            b = i-j+2
                            e = i+j
                if not odd_stop:
                    odd_stop = (i+j >= len(s) or i-j < 0) or s[i+j]!=s[i-j]
                    if odd_stop:
                        if 2*j-1 > e-b:
                            b = i-j+1
                            e = i+j
                if odd_stop and eve_stop:
                    break
        return s[b:e]
```

(python) 76.93%

better one (指 code 方面):

```python
class Solution(object):
    def expandcenter(self, s, left, right):
        while left >=0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return right-left-1
        
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        b = 0
        e = 0
        for i in range(len(s)):
            len1 = self.expandcenter(s, i, i)
            len2 = self.expandcenter(s, i, i+1)
            max_len = max(len1, len2)
            if max_len > e-b:
                print(i, max_len)
                b = i - (max_len-1)//2
                e = i + max_len//2+1
        return s[b:e]
```

(python) 72.21%

## key

* 可使用的方法有
    * brute force `O(n^3)`
    * DP `O(n^2)` with space complexity: `O(n^2)`
    * 中心展開法: `O(n^2)` with space complexity: `O(1)`
    * Manacher's Algorithm: `O(n)`
    
## note

[Editorial Solution](https://leetcode.com/articles/longest-palindromic-substring/)
