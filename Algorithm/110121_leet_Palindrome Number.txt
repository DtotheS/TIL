#9. Palindrome Number (Easy)

- Given an integer x, return true if x is palindrome integer.
- An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.


##Example 1:
'''
Input: x = 121
Output: true
'''
##Example 2:
'''
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
'''
##Example 3:
'''
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
'''
##Example 4:
'''
Input: x = -101
Output: false
''' 

##Constraints:
'''
-231 <= x <= 231 - 1
'''
- Follow up: Could you solve it without converting the integer to a string?

## My Solution

'''
class Solution:
    def isPalindrome(self, x: int) -> bool:
        x = str(x)
        y = []
        y.extend(x)
        z = len(y)
        z2 = z//2
        for i in range(z2):
            if y[i] !=  y[-(i+1)]:
                return False
        return True
'''


## What I learned
- easy but just think about the index. index from beginning start with 0, but from end start with -1. Thus, we cannot simply use y[i] !- y[-i]. 

