# 4. Median of Two Sorted Arrays (Hard)

##Question
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
The overall run time complexity should be O(log (m+n)).

##Example 1:
'''
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
'''
##Example 2:
'''
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
'''
##Example 3:
'''
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
'''
##Example 4:
'''
Input: nums1 = [], nums2 = [1]
Output: 1.00000
'''
##Example 5:
'''
Input: nums1 = [2], nums2 = []
Output: 2.00000
'''

##My Solution
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        #length, not index for list.
        m = len(nums1)
        mm = m//2 # median index. #If odd, later one.
        n = len(nums2)
        nn = n//2
        
        # empty list case check
        if m == 0 and n == 0:
            return None
        elif m == 0:
            if n%2 == 0:
                med2 = (nums2[nn-1]+nums2[nn])/2
            else:
                med2 = nums2[nn]
            return med2
        elif n == 0:
            if m%2 == 0:
                med1 = (nums1[mm]+nums1[mm-1])/2
            else:
                med1 = nums1[mm]
            return med1
        
        #Define median when even or odd.
        if m%2 == 0:
            med1 = (nums1[mm]+nums1[mm-1])/2
        else:
            med1 = nums1[mm]
            
        if n%2 == 0:
            med2 = (nums2[nn-1]+nums2[nn])/2
        else:
            med2 = nums2[nn]
            
        # median is same for the two lists
        if med1 == med2:
            return med1
        


        
        k = m + n
        t1 = 0
        t2 = 0
        final = []
        for i in range(k//2+1):
            if t1 < m and t2 < n:
                if nums1[t1] > nums2[t2]:
                    final.append(nums2[t2])
                    t2 += 1
                else:
                    final.append(nums1[t1])
                    t1 += 1
            elif t1 == m:
                final.extend(nums2[t2:])
            else:
                final.extend(nums1[t1:])
        
        if k%2 == 0:
            return (final[k//2-1]+final[k//2])/2
        else:
            return final[k//2]

## TIL
-Don't think too hard... not that is.
-Check the time complexity.
-use binary search will give O(logn) complexity time.

