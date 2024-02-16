---
layout: default
title: 10 Essential Algorithms
parent: Data Structure and Algorithms
nav_order: 8
---

- [10 Basic Algorithms](#10-basic-algorithms)
- [Here's a LeetCode problem and solution for each of the algorithms:](#heres-a-leetcode-problem-and-solution-for-each-of-the-algorithms)
- [Python code solutions and explanations for each of the LeetCode problems:](#python-code-solutions-and-explanations-for-each-of-the-leetcode-problems)


# 10 Basic Algorithms
1. DFS (Depth-First Search):
   Example: Implement DFS to traverse a graph.
   Solution: 
   ```python
   def dfs(graph, node, visited):
       if node not in visited:
           print(node)
           visited.add(node)
           for neighbor in graph[node]:
               dfs(graph, neighbor, visited)

   # Usage:
   graph = {'A': ['B', 'C'], 'B': ['D', 'E'], 'C': ['F'], 'D': [], 'E': ['F'], 'F': []}
   visited = set()
   dfs(graph, 'A', visited)
   ```

   Time Complexity: O(V + E) where V is the number of vertices, and E is the number of edges.
   Space Complexity: O(V) for the visited set.

2. BFS (Breadth-First Search):
   Example: Implement BFS to traverse a graph.
   Solution:
   ```python
   from collections import deque

   def bfs(graph, start):
       visited = set()
       queue = deque([start])
       while queue:
           node = queue.popleft()
           if node not in visited:
               print(node)
               visited.add(node)
               queue.extend(graph[node] - visited)

   # Usage:
   graph = {'A': {'B', 'C'}, 'B': {'D', 'E'}, 'C': {'F'}, 'D': set(), 'E': {'F'}, 'F': set()}
   bfs(graph, 'A')
   ```

   Time Complexity: O(V + E) where V is the number of vertices, and E is the number of edges.
   Space Complexity: O(V) for the visited set and queue.

3. Matching Parenthesis problem:
   Example: Check if a given string has balanced parentheses.
   Solution:
   ```python
   def is_balanced_parentheses(s):
       stack = []
       for char in s:
           if char in '([{':
               stack.append(char)
           elif char in ')]}':
               if not stack or stack.pop() != '(' and char == ')' or stack.pop() != '[' and char == ']' or stack.pop() != '{' and char == '}':
                   return False
       return not stack

   # Usage:
   print(is_balanced_parentheses("()[]{}"))  # True
   print(is_balanced_parentheses("([)]"))    # False
   ```

   Time Complexity: O(n), where n is the length of the string.
   Space Complexity: O(n) for the stack.

4. Using Hash Tables:
   Example: Count the frequency of elements in an array.
   Solution:
   ```python
   def count_frequency(arr):
       frequency = {}
       for elem in arr:
           if elem in frequency:
               frequency[elem] += 1
           else:
               frequency[elem] = 1
       return frequency

   # Usage:
   arr = [1, 2, 3, 1, 2, 3, 4, 5]
   print(count_frequency(arr))
   ```

   Time Complexity: O(n), where n is the number of elements in the array.
   Space Complexity: O(k), where k is the number of unique elements in the array.

5. Variables/Pointers Manipulation:
   Example: Swap two variables without using a temporary variable.
   Solution:
   ```python
   def swap(a, b):
       a = a + b
       b = a - b
       a = a - b
       return a, b

   # Usage:
   x = 5
   y = 10
   x, y = swap(x, y)
   print(x, y)
   ```

   Time Complexity: O(1)
   Space Complexity: O(1)

6. Reverse Linked List (with duplicates and removing duplicates):
   Example: Reverse a singly linked list.
   Solution:
   ```python
   class ListNode:
       def __init__(self, val=0, next=None):
           self.val = val
           self.next = next

   def reverse_linked_list(head):
       prev = None
       current = head
       while current:
           next_node = current.next
           current.next = prev
           prev = current
           current = next_node
       return prev

   # Usage:
   # Assume you have a linked list: 1 -> 2 -> 3 -> 4 -> 5
   # Reverse it as follows:
   head = ListNode(1, ListNode(2, ListNode(3, ListNode(4, ListNode(5)))))
   new_head = reverse_linked_list(head)
   ```

   Time Complexity: O(n), where n is the number of nodes in the linked list.
   Space Complexity: O(1)

7. Sorting Fundamentals (Quicksort, Mergesort, Bubblesort):
   Example: Implement Quicksort to sort an array.
   Solution:
   ```python
   def quicksort(arr):
       if len(arr) <= 1:
           return arr
       pivot = arr[len(arr) // 2]
       left = [x for x in arr if x < pivot]
       middle = [x for x in arr if x == pivot]
       right = [x for x in arr if x > pivot]
       return quicksort(left) + middle + quicksort(right)

   # Usage:
   arr = [3, 6, 8, 10, 1, 2, 1]
   sorted_arr = quicksort(arr)
   print(sorted_arr)
   ```

   Time Complexity: O(n log n) in average and best cases, O(n^2) in the worst case.
   Space Complexity: O(log n) in average and best cases, O(n) in the worst case.

   Mergesort and Bubblesort can also be implemented similarly. Mergesort has a consistent O(n log n) time complexity, while Bubblesort has a worst-case time complexity of O(n^2).

8. Recursion:
   Example: Implement a recursive function to calculate the factorial of a number.
   Solution:
   ```python
   def factorial(n):
       if n == 0:
           return 1
       else:
           return n * factorial(n - 1)

   # Usage:
   result = factorial(5)  # Calculates 5!
   ```

   Time Complexity: O(n)
   Space Complexity: O(n) due to the recursive call stack.

9. Custom Data Structures (Object-Oriented Programming):
   Example: Implement a custom Stack data structure.
   Solution:
   ```python
   class Stack:
       def __init__(self):
           self.items = []

       def push(self, item):
           self.items.append(item)

       def pop(self):
           if not self.is_empty():
               return self.items.pop()
           else:
               return None

       def is_empty(self):
           return len(self.items) == 0

   # Usage:
   stack = Stack()
   stack.push(1)
   stack.push(2)
   print(stack.pop())  # Outputs 2
   ```

   Time Complexity: O(1) for push, pop, and is_empty operations.
   Space Complexity: O(n), where n is the number of elements in the stack.

10. Binary Search:
    Example: Implement binary search to find an element in a sorted array.
    Solution:
    ```python
    def binary_search(arr, target):
        left, right = 0, len(arr) - 1
        while left <= right:
            mid = (left + right) // 2
            if arr[mid] == target:
                return mid
            elif arr[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return -1

    # Usage:
    arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    target = 5
    result = binary_search(arr, target)  # Returns the index of 5 in the array.
    ```

    Time Complexity: O(log n), where n is the number of elements in the array.
    Space Complexity: O(1).

These examples should help you practice and understand these fundamental algorithms commonly used in coding interviews for a metadata engineer position at Meta or any other tech company.

# Here's a LeetCode problem and solution for each of the algorithms:

1. DFS (Depth-First Search):
   LeetCode Problem: [Number of Islands](https://leetcode.com/problems/number-of-islands/)
   Solution: [Number of Islands Solution](https://leetcode.com/problems/number-of-islands/solution/)

2. BFS (Breadth-First Search):
   LeetCode Problem: [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
   Solution: [Binary Tree Level Order Traversal Solution](https://leetcode.com/problems/binary-tree-level-order-traversal/solution/)

3. Matching Parenthesis Problem:
   LeetCode Problem: [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
   Solution: [Valid Parentheses Solution](https://leetcode.com/problems/valid-parentheses/solution/)

4. Using Hash Tables:
   LeetCode Problem: [Two Sum](https://leetcode.com/problems/two-sum/)
   Solution: [Two Sum Solution](https://leetcode.com/problems/two-sum/solution/)

5. Variables/Pointers Manipulation:
   LeetCode Problem: [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)
   Solution: [Swap Nodes in Pairs Solution](https://leetcode.com/problems/swap-nodes-in-pairs/solution/)

6. Reverse Linked List (with Duplicates and Removing Duplicates):
   LeetCode Problem (Reverse Linked List): [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
   Solution (Reverse Linked List): [Reverse Linked List Solution](https://leetcode.com/problems/reverse-linked-list/solution/)
   
   LeetCode Problem (Remove Duplicates from Sorted List): [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
   Solution (Remove Duplicates from Sorted List): [Remove Duplicates from Sorted List Solution](https://leetcode.com/problems/remove-duplicates-from-sorted-list/solution/)

7. Sorting Fundamentals (Quicksort, Mergesort, Bubblesort):
   LeetCode Problem (Quicksort): [Sort an Array](https://leetcode.com/problems/sort-an-array/)
   Solution (Quicksort): You can use the quicksort implementation provided earlier.

   LeetCode Problem (Mergesort): [Sort List](https://leetcode.com/problems/sort-list/)
   Solution (Mergesort): [Sort List Solution](https://leetcode.com/problems/sort-list/solution/)

   LeetCode Problem (Bubblesort): There isn't a specific problem for Bubblesort, as it's not an efficient sorting algorithm. Use other sorting algorithms for real-world problems.

8. Recursion:
   LeetCode Problem: [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)
   Solution: [Fibonacci Number Solution](https://leetcode.com/problems/fibonacci-number/solution/)

9. Custom Data Structures (Object-Oriented Programming):
   LeetCode Problem: [Min Stack](https://leetcode.com/problems/min-stack/)
   Solution: [Min Stack Solution](https://leetcode.com/problems/min-stack/solution/)

10. Binary Search:
    LeetCode Problem: [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
    Solution: [Search in Rotated Sorted Array Solution](https://leetcode.com/problems/search-in-rotated-sorted-array/solution/)

These LeetCode problems and their solutions will allow you to practice and apply the corresponding algorithms in real coding scenarios.

# Python code solutions and explanations for each of the LeetCode problems:

1. DFS (Depth-First Search):
   Problem: [Number of Islands](https://leetcode.com/problems/number-of-islands/)
   Solution:
   ```python
   def numIslands(grid):
       if not grid:
           return 0

       def dfs(i, j):
           if i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] == '0':
               return
           grid[i][j] = '0'  # Mark the current cell as visited
           # Visit adjacent cells
           dfs(i - 1, j)
           dfs(i + 1, j)
           dfs(i, j - 1)
           dfs(i, j + 1)

       count = 0
       for i in range(len(grid)):
           for j in range(len(grid[0])):
               if grid[i][j] == '1':
                   count += 1
                   dfs(i, j)
       return count
   ```
   Explanation: This code uses DFS to count the number of islands in a 2D grid. It starts from each '1' cell and explores all adjacent '1' cells, marking them as '0' to indicate visited.

2. BFS (Breadth-First Search):
   Problem: [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
   Solution:
   ```python
   from collections import deque

   def levelOrder(root):
       if not root:
           return []

       result = []
       queue = deque([root])

       while queue:
           level_vals = []
           level_size = len(queue)

           for _ in range(level_size):
               node = queue.popleft()
               level_vals.append(node.val)

               if node.left:
                   queue.append(node.left)
               if node.right:
                   queue.append(node.right)

           result.append(level_vals)

       return result
   ```
   Explanation: This code performs level-order traversal of a binary tree using BFS. It uses a queue to keep track of nodes at each level and processes them one level at a time.

3. Matching Parenthesis Problem:
   Problem: [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
   Solution:
   ```python
   def isValid(s):
       stack = []
       mapping = {')': '(', '}': '{', ']': '['}

       for char in s:
           if char in mapping:
               top_element = stack.pop() if stack else '#'
               if mapping[char] != top_element:
                   return False
           else:
               stack.append(char)

       return not stack
   ```
   Explanation: This code checks if the input string has valid parentheses by using a stack to keep track of opening and closing brackets. It pops the stack when a closing bracket is encountered and checks if it matches the corresponding opening bracket.

4. Using Hash Tables:
   Problem: [Two Sum](https://leetcode.com/problems/two-sum/)
   Solution:
   ```python
   def twoSum(nums, target):
       num_to_index = {}
       for i, num in enumerate(nums):
           complement = target - num
           if complement in num_to_index:
               return [num_to_index[complement], i]
           num_to_index[num] = i
       return None
   ```
   Explanation: This code finds two numbers in an array that add up to the given target. It uses a dictionary to store the numbers and their indices, and then checks for the complement (target - current number) in the dictionary.

5. Variables/Pointers Manipulation:
   Problem: [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)
   Solution:
   ```python
   class ListNode:
       def __init__(self, val=0, next=None):
           self.val = val
           self.next = next

   def swapPairs(head):
       dummy = ListNode(0)
       dummy.next = head
       prev = dummy

       while head and head.next:
           first_node = head
           second_node = head.next

           prev.next = second_node
           first_node.next = second_node.next
           second_node.next = first_node

           prev = first_node
           head = first_node.next

       return dummy.next
   ```
   Explanation: This code swaps pairs of nodes in a linked list by manipulating pointers. It uses a dummy node to simplify the process and iterates through the list while swapping adjacent nodes.

6. Reverse Linked List (with Duplicates and Removing Duplicates):
   Problem (Reverse Linked List): [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
   Solution (Reverse Linked List):
   ```python
   class ListNode:
       def __init__(self, val=0, next=None):
           self.val = val
           self.next = next

   def reverseList(head):
       prev = None
       current = head
       while current:
           next_node = current.next
           current.next = prev
           prev = current
           current = next_node
       return prev
   ```
   Problem (Remove Duplicates from Sorted List): [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
   Solution (Remove Duplicates from Sorted List):
   ```python
   class ListNode:
       def __init__(self, val=0, next=None):
           self.val = val
           self.next = next

   def deleteDuplicates(head):
       current = head
       while current and current.next:
           if current.val == current.next.val:
               current.next = current.next.next
           else:
               current = current.next
       return head
   ```
   Explanation: The first code snippet reverses a singly linked list by changing the direction of pointers. The second code snippet removes duplicates from a sorted linked list by updating pointers to skip duplicates.

7. Sorting Fundamentals (Quicksort, Mergesort, Bubblesort):
   Problem (Quicksort): [Sort an Array](https://leetcode.com/problems/sort-an-array/)
   Solution (Quicksort):
   ```python
   def sortArray(nums):
       if len(nums) <= 1:
           return nums

       pivot = nums[len(nums) // 2]
       left = [x for x in nums if x < pivot]
       middle = [x for x in nums if x == pivot]
       right = [x for x in nums if x > pivot]

       return sortArray(left) + middle + sortArray(right)
   ```
   Problem (Mergesort): [Sort List](https://leetcode.com/problems/sort-list/)
   Solution (Mergesort):
   ```python
   class ListNode:
       def __init__(self, val=0, next=None):
           self.val = val
           self.next = next

   def sortList(head):
       if not head or not head.next:
           return head

       mid = self.find_middle(head)
       left = head
       right = mid.next
       mid.next = None

       left_sorted = self.sortList(left)
       right_sorted = self.sortList(right)

       return self.merge(left_sorted, right_sorted)

   def find_middle(self, head):
       slow = head
       fast = head
       while fast.next and fast.next.next:
           slow = slow.next
           fast = fast.next.next
       return slow

   def merge(self, left, right):
       dummy = ListNode(0)
       current = dummy

       while left and right:
           if left.val < right.val:
               current.next = left
               left = left.next
           else:
               current.next = right
               right = right.next
           current = current.next

       if left:
           current.next = left
       if right:
           current.next = right

       return dummy.next
   ```
   Explanation: The first code snippet implements Quicksort for an array, and the second code snippet implements Mergesort for a linked list. Both sorting algorithms use the divide-and-conquer approach.

8. Recursion:
   Problem: [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)
   Solution:
   ```python
   def fib(n):
       if n <= 1:
           return n
       return fib(n - 1) + fib(n - 2)
   ```
   Explanation: This code calculates the nth Fibonacci number using recursion. It breaks the problem down into smaller subproblems until it reaches the base cases.

9. Custom Data Structures (Object-Oriented Programming):
   Problem: [Min Stack](https://leetcode.com/problems/min-stack/)
   Solution:
   ```python
   class MinStack:

       def __init__(self):
           self.stack = []
           self.min_stack = []

       def push(self, val: int) -> None:
           self.stack.append(val)
           if not self.min_stack or val <= self.min_stack[-1]:
               self.min_stack.append(val)

       def pop(self) -> None:
           if self.stack:
               if self.stack[-1] == self.min_stack[-1]:
                   self.min_stack.pop()
               self.stack.pop()

       def top(self) -> int:
           if self.stack:
               return self.stack[-1]

       def getMin(self) -> int:
           if self.min_stack:
               return self.min_stack[-1]
   ```
   Explanation: This code implements a custom MinStack data structure that supports push, pop, top, and getMin operations. It uses two stacks, one to store values and another to store the minimum values seen so far.

10. Binary Search:
    Problem: [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
    Solution:
    ```python
    def search(nums, target):
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                return mid
            if nums[left] <= nums[mid]:
                if nums[left] <= target < nums[mid]:
                    right = mid - 1
                else:
                    left = mid + 1
            else:
                if nums[mid] < target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid - 1
        return -1
    ```
    Explanation: This code performs binary search in a rotated sorted array. It checks which half of the array is sorted and determines if the target is in that half, updating the search range accordingly.

These explanations and solutions should help you understand how to apply each algorithm to various real-world problems on LeetCode.