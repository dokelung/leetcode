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

## key

## note
