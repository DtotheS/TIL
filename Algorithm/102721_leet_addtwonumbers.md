# 2. Add Two Numbers (Medium)

## Question
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Example 1:
"leet_2.jpg"

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```
## Example 2:
```
Input: l1 = [0], l2 = [0]
Output: [0]
```
##Example 3:
```
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```

## My solution
The counter example is when the lenth of two lists are different. Thus, I will put 0s at the end of the shorter list and make them same length. Then, we can sum from back. 

```
ex. [4,3,2,1] vs. [3,2,1] (1234 + 123=1357) => [4,3,2,1] vs. [3,2,1,0] => [7,5,3,1]

## Definition for singly-linked list.
## class ListNode:
##     def __init__(self, val=0, next=None):
##         self.val = val
##         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        list1=[]
        list2=[]
        while l1:
            list1.append(l1.val)
            l1 = l1.next
        while l2:
            list2.append(l2.val)
            l2 = l2.next

        if len(list1) > len(list2):
            foo2 = len(list1)-len(list2)
            foo3 = [0]*foo2
            list2.extend(foo3)
        elif len(list1) < len(list2):
            foo2 = len(list2)-len(list1)
            foo3 = [0]*foo2
            list1.extend(foo3)
            
        mlen = len(list1)
        output = []
        
        for i in range(mlen-1):
            sum = list1[i] + list2[i]
            if sum < 10:
                output.append(sum)
            else:
                sum = sum - 10
                output.append(sum)
                list1[i+1] = list1[i+1]+1
        sum = list1[mlen-1] + list2[mlen-1]
        if sum < 10:
            output.append(sum)
        else:
            output.append(sum-10)
            output.append(1)
        d = ["k{0}".format(i) for i in range(len(output))]
        for i in range(len(d)):
            d[i] = ListNode()       
        for i in range(len(d)):
            if i < len(d)-1:
                d[i].val = output[i]
                d[i].next = d[i+1]
            else:
                d[i].val = output[i]
        return d[0]
```

## Learns
- Concept of "Linked List" is critical.

- Keep in mind that object of Class can be an argument another Class (or object), so that we can connect two classes or objects.

- (:) within function argument means argument annotation. (->) within function means return annotation.

- Type Union[x,y,z] == x|y|z == either x or y or z
- Type Optional[x] == Union[x,None] == either x or None.

- .append(): Adds its argument as a single element to the end of a list. The length of the list increases by one. NOTE: A list is an object. If you append another list onto a list, the parameter list will be a single object at the end of the list.
```
my_list = ['geeks', 'for']
my_list.append('geeks')
print my_list
output = ['geeks', 'for', 'geeks']
```
- .extend(): Iterates over its argument and adding each element to the list and extending the list. The length of the list increases by number of elements in it’s argument. NOTE: A string is an iterable, so if you extend a list with a string, you’ll append each character as you iterate over the string.

- Time Complexity
- Append has constant time complexity i.e.,O(1).
- Extend has time complexity of O(k). Where k is the length of list which need to be added.

-Using Optional[] arguments when defining function.

-define function: https://www.w3schools.com/python/python_functions.asp
```
def my_function():

```
- *arg : do not know how many arguments
- **keywords : do not know how many keywords
- Can set Default Parameter Value def my_function(country = "Norway"):

- Lastly, I struggled making final answers. 
- Why it is not working: k1 = ListNode(0,None), k1 = Listnode(10, k2). Then, why not later k1 overlaps the first one? Because of this, I spent a lot of time..... Got it.
```
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
        
k1 = ListNode()
k2 = ListNode()
k3 = ListNode()
k1 = ListNode(10,k2)
k2 = ListNode(4,k3)
a = k1.next
print(a.val)
```
- Here, when I make a k1 class, it is using previous k2 = ListNode(). Even though I redefined k2 after, it was not applied for k1 class....






