# 5.  Longest Palindromic Substring (Medium)

## Given a string  `s`, return _the longest palindromic substring_  in  `s`.
```
Example 1:
Input: s = "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```
```
Example 2:

Input: s = "cbbd"
Output: "bb"
```
```
Example 3:

Input: s = "a"
Output: "a"
```
```
Example 4:

Input: s = "ac"
Output: "a"
```
```
Constraints:
`1 <= s.length <= 1000`
`s`  consist of only digits and English letters.
```

## My Solution 1: Brute-Force (Time out)
```
class Solution:
    def longestPalindrome(self, s: str) -> str:
        li = []
        li.extend(s)
        pali = []
        
        for i in range(len(li)):
            for j in reversed(range(i,len(li))):
                ss = i
                ee = j
                while li[ss] == li[ee]:
                    if ee-ss <= 1:
                        foo = [li[k] for k in range(i,j+1)]
                        pali.append(foo)
                        break
                    else:
                        ss += 1
                        ee += -1
        
        len_v = [len(ele) for ele in pali]
        max_val = max(len_v)
        max_index = len_v.index(max_val)
        ans = "".join(pali[max_index])
        return ans
```

## My solution 2: Based on hint
## TIL
- Use of string.join(iterable) method in python
- need to think when to break in while loop.
- reversed(range(10)) can be used reversed order looping.