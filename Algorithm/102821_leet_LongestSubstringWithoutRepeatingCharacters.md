#3. Longest Substring Without Repeating Characters(Medium)

##Given a string s, find the length of the longest substring without repeating characters.

 

##Example 1:
'''
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

##Example 2:
'''
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
'''

##Example 3:
'''
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
'''

##Example 4:
'''
Input: s = ""
Output: 0
'''

##Constraints:
'''
0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.
'''

## My solution (bad speed and memory)
'''
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if s is False:
            return 0
        li = []
        li.extend(s)
        long = len(li)
        if long == 0:
            return 0
        if long == 1:
            return 1
        
        outputs = []
        for i in range(long):
            count = 0
            if i == long:
                outputs.append(1)
            else:
                for j in range(i+1,long):
                    count += 1
                    if li[i] == li[j]:
                        outputs.append(count)
                        break
                    elif j == long-1:
                        count += 1
                        outputs.append(count)
                        break
        outputs.append(1)
        # return(print(outputs))
 
        for i in range(len(outputs)-1):
            foo = []
            for j in range(i+1,i+outputs[i]):
                if outputs[j] < outputs[i]-j+i:
                    foo.append(outputs[j]+j-i)
                    # if j-1 < outputs[j]:
                    # if outputs[j]+j-1>outputs[i]:
            if foo:
                outputs[i] = min(foo)
            # else:
                # outputs[i] = outputs[i]-1
        return max(outputs)
'''


### What I learned
- First, need to carefully decide what I will use as a criterion and keep consistent
-- For example: abcabcddbb
-- Option 1: use longest strings = [3,3,...] 
-- Option 2: use the length which firstly repeated string show up. = [4,4, ...] => in this case, if there is no repeated measure, then it can cause some problems. Thus, we need to careful to define the variable.
- think about the outlier cases .
- Think about the idea of exclude, include, and overlapped sets.
