---
layout: default
title: Basic Python Method
parent: Data Structure and Algorithms
nav_order: 8
---


### 1. Container Types

#### List
A list is an ordered collection of items that can be modified (mutable). It can contain items of different types.
```python
my_list = [1, 'apple', 3.14]
print(my_list[1])  # Output: apple
my_list.append('banana')
print(my_list)  # Output: [1, 'apple', 3.14, 'banana']
```

#### Tuple
A tuple is similar to a list but immutable. Once created, items cannot be added or removed.
```python
my_tuple = (1, 'apple', 3.14)
print(my_tuple[1])  # Output: apple
```

#### Dictionary
A dictionary is an unordered collection of items. Each item is stored as a key-value pair. Dictionaries are mutable.
```python
my_dict = {'name': 'John', 'age': 30}
print(my_dict['name'])  # Output: John
my_dict['age'] = 31
print(my_dict)  # Output: {'name': 'John', 'age': 31}
```

#### Set
A set is an unordered collection of unique items. Sets are mutable but only store unique values.
```python
my_set = {1, 2, 3, 2}
print(my_set)  # Output: {1, 2, 3}
my_set.add(4)
print(my_set)  # Output: {1, 2, 3, 4}
```

### 2. Conversions

#### String to List
```python
my_string = "hello world"
my_list = list(my_string)
print(my_list)  # Output: ['h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
```

#### Split Words into List
```python
words = "hello world".split()
print(words)  # Output: ['hello', 'world']
```

#### Join String
```python
words = ['hello', 'world']
joined_string = ' '.join(words)
print(joined_string)  # Output: hello world
```

#### List to Set
```python
my_list = [1, 2, 2, 3, 4]
my_set = set(my_list)
print(my_set)  # Output: {1, 2, 3, 4}
```

### 3. List Indexing

Lists can be indexed using both positive and negative numbers. `0` refers to the first item, and `-1` refers to the last item.
```python
my_list = [10, 20, 30, 40, 50]
print(my_list[0])  # Output: 10
print(my_list[-1])  # Output: 50
```

### 4. Exceptions on Errors

Exceptions are used to handle errors in Python. You can catch exceptions using a try-except block.
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

### 5. Math Operations

Basic math operations include addition (`+`), subtraction (`-`), multiplication (`*`), division (`/`), modulus (`%`), exponentiation (`**`), and floor division (`//`).
```python
print(5 + 2)  # Output: 7
print(5 ** 2)  # Output: 25
print(8 / 3)  # Output: 2.666...
print(8 // 3)  # Output: 2
```

### 6. Boolean Logic

Boolean operations include `and`, `or`, `not`, and comparison operators like `<`, `>`, `==`, `!=`.
```python
print(True and False)  # Output: False
print(True or False)  # Output: True
print(not False)  # Output: True
print(5 > 3)  # Output: True
print(5 == 5)  # Output: True
print(5 != 3)  # Output: True
```

### 7. Integer Sequence: `range`

The `range` function generates a sequence of integers. It is often used in loops.
```python
for i in range(0, 5):
    print(i)
# Output: 0 1 2 3 4
```

### 8. Generic Operations on Containers

#### `len`
Returns the number of items in a container.
```python
print(len([1, 2, 3]))  # Output: 3
```

#### `min` and `max`
Return the smallest and largest items, respectively.
```python
print(min([1, 2, 3]))  # Output: 1
print(max([1, 2, 3]))  # Output: 3
```

#### `sum`
Returns the sum of a container's items.
```python
print(sum([1, 2, 3]))  # Output: 6
```

#### `sorted`
Returns a new sorted list from the elements of any iterable.
```python
print(sorted([3, 1, 2]))  # Output: [1, 2, 3]
```

#### `in`
Checks if an item exists within a container.
```python
print(2 in [1, 2, 3])  # Output: True
```

#### `enumerate`
Yields pairs containing a count (from start, which defaults to 0) and values obtained from iterating over an iterable.
```python
for index, value in enumerate(["a", "b", "c"]):
    print(index, value)
# Output: 0 a 1 b 2 c
```

#### `zip`
Combines elements from multiple iterables into tuples.
```python
for a, b in zip([1, 2, 3], ['a', 'b', 'c']):
    print(a, b)
# Output: 1 a 2 b 3 c
```

#### `all`
Returns True if all elements of the iterable are true (or if the iterable is empty).
```python
print(all([True, True, False]))  # Output: False
```

#### `any`
Returns True if any element of the iterable is true. If the iterable is empty, return False.
```python
print(any([False, False, True]))  # Output: True
```

### 9. Operations for Ordered Sequences Containers (list, string, tuples)

#### `reversed`
Returns a reverse iterator.
```python
print(list(reversed([1, 2, 3])))  # Output: [3, 2, 1]
```

#### `*`
Concatenates a repeated sequence.
```python
print([1, 2] * 2)  # Output: [1, 2, 1, 2]
```

#### `+`
Concatenates sequences.
```python
print([1, 2] + [3, 4])  # Output: [1, 2, 3, 4]
```

#### `index`
Finds the first occurrence of a value.
```python
print([1, 2, 3].index(2))  # Output: 1
```

#### `count`
Counts the occurrences of a value.
```python
print([1, 2, 2, 3].count(2))  # Output: 2
```

### 10. Operations on Lists

#### `append`
Adds an item to the end.
```python
lst = [1, 2]
lst.append(3)
print(lst)  # Output: [1, 2, 3]
```

#### `extend`
Adds all elements of an iterable to the list.
```python
lst = [1, 2]
lst.extend([3, 4])
print(lst)  # Output: [1, 2, 3, 4]
```

#### `insert`
Inserts an item at a given position.
```python
lst = [1, 2]
lst.insert(1, 'a')
print(lst)  # Output: [1, 'a', 2]
```

#### `remove`
Removes the first occurrence of a value.
```python
lst = [1, 2, 3, 2]
lst.remove(2)
print(lst)  # Output: [1, 3, 2]
```

#### `pop`
Removes and returns an item at a given position.
```python
lst = [1, 2, 3]
print(lst.pop(1))  # Output: 2
print(lst)  # Output: [1, 3]
```

#### `sort`
Sorts the list in place.
```python
lst = [

3, 1, 2]
lst.sort()
print(lst)  # Output: [1, 2, 3]
```

#### `reverse`
Reverses the list in place.
```python
lst = [1, 2, 3]
lst.reverse()
print(lst)  # Output: [3, 2, 1]
```

### 11. Operations on Dictionaries

#### `update`
Updates the dictionary with elements from another dictionary or from an iterable of key-value pairs.
```python
dct = {'a': 1}
dct.update({'b': 2})
print(dct)  # Output: {'a': 1, 'b': 2}
```

#### `keys`, `values`, `items`
Return views of the dictionary's keys, values, and key-value pairs.
```python
dct = {'a': 1, 'b': 2}
print(list(dct.keys()))  # Output: ['a', 'b']
print(list(dct.values()))  # Output: [1, 2]
print(list(dct.items()))  # Output: [('a', 1), ('b', 2)]
```

#### `pop`
Removes a key from the dictionary and returns its value.
```python
dct = {'a': 1, 'b': 2}
print(dct.pop('a'))  # Output: 1
print(dct)  # Output: {'b': 2}
```

#### `popitem`
Removes and returns a (key, value) pair as a 2-tuple.
```python
dct = {'a': 1, 'b': 2}
print(dct.popitem())  # Output: ('b', 2)
```

#### `get`
Returns the value for a key if it exists, otherwise a default value.
```python
dct = {'a': 1}
print(dct.get('a', 'not found'))  # Output: 1
print(dct.get('b', 'not found'))  # Output: not found
```

#### `setdefault`
Returns the value of a key if it is in the dictionary; if not, inserts the key with a specified value.
```python
dct = {'a': 1}
print(dct.setdefault('a', 'default'))  # Output: 1
print(dct.setdefault('b', 'default'))  # Output: default
print(dct)  # Output: {'a': 1, 'b': 'default'}
```

### 12. Operations on Sets

#### `update`
Adds elements from another set or iterable to the set.
```python
st = {1, 2}
st.update([3, 4])
print(st)  # Output: {1, 2, 3, 4}
```

#### `copy`
Returns a shallow copy of the set.
```python
st = {1, 2}
cpy = st.copy()
print(cpy)  # Output: {1, 2}
```

#### `add`
Adds an element to the set.
```python
st = {1, 2}
st.add(3)
print(st)  # Output: {1, 2, 3}
```

#### `remove`
Removes an element from the set. Raises a KeyError if the element is not present.
```python
st = {1, 2, 3}
st.remove(2)
print(st)  # Output: {1, 3}
```

#### `discard`
Removes an element from the set if it is a member. If the element is not a member, do nothing.
```python
st = {1, 2, 3}
st.discard(3)
print(st)  # Output: {1, 2}
```

#### `clear`
Removes all elements from the set.
```python
st = {1, 2, 3}
st.clear()
print(st)  # Output: set()
```

#### `pop`
Removes and returns an arbitrary element from the set. Raises KeyError if the set is empty.
```python
st = {1, 2, 3}
print(st.pop())  # Output: 1 (or 2, 3 - arbitrary)
print(st)  # Remaining set after an element is popped
```


### 13. Function Definition: `*args`, `**kwargs`

- `*args` allows a function to accept any number of positional arguments, while `**kwargs` allows it to accept any number of keyword arguments.

```python
def my_function(*args, **kwargs):
    print("args:", args)
    print("kwargs:", kwargs)

my_function(1, 2, 3, name="John", age=30)
# Output:
# args: (1, 2, 3)
# kwargs: {'name': 'John', 'age': 30}
```

### 14. `copy` and `deepcopy`

- `copy` creates a shallow copy of an object, while `deepcopy` creates a deep copy, duplicating any nested objects.

```python
import copy

lst1 = [[1, 2, 3], [4, 5, 6]]
lst2 = copy.copy(lst1)
lst3 = copy.deepcopy(lst1)

lst1[0][0] = 'X'

print(lst2)  # Shallow copy reflects changes to nested objects
print(lst3)  # Deep copy does not reflect changes
```

### 15. String Operations

Here are brief explanations and examples for common string operations:

#### `startswith`, `endswith`

```python
s = "Hello world"
print(s.startswith("Hello"))  # True
print(s.endswith("world"))    # True
```

#### `count`

```python
s = "banana"
print(s.count("a"))  # 3
```

#### `index`

```python
s = "Hello world"
print(s.index("world"))  # 6
```

#### `isalpha`, `isdigit`, etc.

```python
print("abc".isalpha())  # True
print("123".isdigit())  # True
print("abc123".isalnum())  # True
```

#### `strip`, `rstrip`, `lstrip`

```python
s = "   Hello world   "
print(s.strip())  # "Hello world"
print(s.rstrip()) # "   Hello world"
print(s.lstrip()) # "Hello world   "
```

#### `partition`
partition(sep) splits the string at the first occurrence of the separator sep.
It returns a tuple of three elements: the part before the separator, the separator itself (if found; otherwise, an empty string), and the part after the separator.

```python
s = "Hello world"
print(s.partition(" "))  # ('Hello', ' ', 'world')
```

#### `find`

```python
s = "Hello world"
print(s.find("world"))  # 6
print(s.find("Python")) # -1, because "Python" is not found
```

#### `upper`, `lower`, `title`, `swapcase`, `casefold`, `capitalize`

```python
s = "Hello world"
print(s.upper())    # "HELLO WORLD"
print(s.lower())    # "hello world"
print(s.title())    # "Hello World"
print(s.swapcase()) # "hELLO WORLD"
print(s.casefold()) # "hello world", similar to lower() but more aggressive
print(s.capitalize()) # "Hello world"
```

#### `center`, `ljust`, `rjust`

```python
s = "Hello"
print(s.center(10))  # "  Hello   "
print(s.ljust(10))   # "Hello     "
print(s.rjust(10))   # "     Hello"
```

#### `zfill`

```python
s = "42"
print(s.zfill(5))  # "00042"
```

#### `encode`

```python
s = "Hello world"
print(s.encode("utf-8"))  # b'Hello world', byte representation of the string
```

#### `split`

```python
s = "Hello world"
print(s.split())      # ['Hello', 'world']
print(s.split("o"))   # ['Hell', ' w', 'rld']
```

#### `join`

```python
words = ["Hello", "world"]
print(" ".join(words))  # "Hello world"
print(", ".join(words)) # "Hello, world"
```


### 16. Formatting

- `"{}".format()` and f-strings (Python 3.6+) are common ways to format strings. The `.format()` method inserts the specified values into the string's placeholder.

```python
print("{} and {}".format("apple", "banana"))
# Output: apple and banana

# Advanced formatting with format specification
print("{:,.2f}".format(1234.5678))
# Output: '1,234.57' - number formatted with a comma as a thousand separator and rounded to two decimal places.
```

### 17. List Sort with Lambda Function

- Sorting with a lambda function as the key allows custom sort criteria.

```python
lst = [('apple', 2), ('banana', 1), ('cherry', 3)]
lst.sort(key=lambda x: x[1], reverse=True)
print(lst)  # [('cherry', 3), ('apple', 2), ('banana', 1)]
```

### 18. List with Map Function

- `map` applies a function to all items in an input list. A common use is with a lambda function for concise transformations.

```python
numbers = [1, 2, 3, 4]
sqr_numbers = list(map(lambda x: x**2, numbers))
print(sqr_numbers)  # [1, 4, 9, 16]
```

These examples and explanations cover a wide range of Python's functionality, from basic data manipulation to more complex operations involving functions and data structures, providing a solid foundation for understanding and using Python effectively.