# Built-in-Data-Structure-in-Python

- [List](#list)
- [Deque](#deque)
- [Tuple](#tuple)
- [Dictionary](#dictionary)
- [Default Dictionary](#default-dictionary)
- [Set](#set)
- [Frozenset](#frozenset)
- [Counter](#counter)
- [heapq](#heapq)

## List 
- Python's list (Mutable) are implemented as dynamic arrays behind the scenes.
- Arrays store information in adjoining blocks of memory.
- Python List cab be hold arbitrary elements.
- It's very fast (O(1) -> Constant Time) for accessing, updating, adding (Only in the last position) and removing (Only in the last position) data. 
- But It's not a good choice for adding & removing data except in the last position of list. We can use deque for that.
>Useful Methods: index()/count()/append()/pop()/pop(index)/insert()/remove()/clear()/sort()/reverse()/extend()/copy()
> [1,2,3,4,5]

#### List Comprehension
```python
li = [1,2,3,4,5]
bigger = [num for num in li if num > 3]
# Output: [4,5]
```
#### List as Stack
Supports append and pop operations in O(1) time
```python
user = []
# Insert user in the Last of List
user.append('John')
user.append('Justin')
user.append('Foo')
print(user) # ['John', 'Justin', 'Foo']

# Remove user from the Last of List
user.pop()
print(user) # ['John', 'Justin']
user.pop()
print(user) # ['John']
```
#### List as Queue
Supports append and pop operations in O(n) time. We can optimized the performance using deque data structure.
```python
user = []
# Insert user in the Last of List
user.append('John')
user.append('Justin')
user.append('Foo')
print(user) # ['John', 'Justin', 'Foo']

# Remove user from the first of List
user.pop(0)
print(user) # ['Justin', 'Foo']
user.pop(0)
print(user) # ['Foo']
```

## Deque
- The deque class implements a double-ended queue
- supports adding and removing elements from either end in O(1) time
>Useful Methods: append(x)/appendleft(x)/clear()/copy()/count(x)/extend(iterable)/extendleft(iterable)/index()/insert(i,x)/pop()/popleft()/remove(x)/reverse()/rotate(n=1)/maxlen()
```python
from collections import deque

li = ['John', 'Doe', 'Foo', 'Bar']
dq = deque(li)
print(dq)
# deque(['John', 'Doe', 'Foo', 'Bar'])

dq.appendleft('Justin') # Add data in first position on constant time O(1)
print(dq) # deque(['Justin', 'John', 'Doe', 'Foo', 'Bar'])

dq.popleft() # Remove data in first position on constant time O(1)
print(dq) # deque(['John', 'Doe', 'Foo', 'Bar'])
```
## Tuple 
- If we want to store no-changeable data, tuple (Immutable) is a good choice for that.
- We can't add, update, remove data, only can read data of Tuple.
>Useful Methods: index(x), count(x)
```python
tpl = (1,2,3,4)
```
```python
# Create a Generator using Tuple Comprehension
users = ("Joe", "John", "Root", "Justin", "Foo")
gen = (item for item in users)
print(type(gen)) # Output: <class 'generator'>
```
## Dictionary 
- Also known as maps, hashmaps, lookup tables, associative arrays
- Efficient Lookup, insertion and deletion
>Useful Methods: get(x), pop(x), clear(), keys(dict), values(dict), items(dict), copy()

#### Dictionary Comprehension
```python
nums = {x: x * x for x in range(1, 6)}
print(nums)
# Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```
#### Access & Add Data in Dictionary
```python 
# Access the Data
person = { 'name': 'John Doe', 'country': 'usa', 'age': 30 }
print(person['name']) # Output: John Doe
print(person['country']) # Output: usa
print(person.get('name')) # Output: John Doe

# Add the Data
person = { 'name': 'John Doe', 'country': 'usa', 'age': 30 }
person['city'] = 'New York'
print(person) 
# Output: {'name': 'John Doe', 'country': 'usa', 'age': 30, 'city': 'New York'}
```
## Default Dictionary 
- The defaultdict (Return Default Values for Missing Keys) class is another dictionary subclass that accepts a callable in its constructor
- It returns a default value if the requested key can not be found.
```python
from collections import defaultdict

dd = defaultdict(list)
dd['dogs'].append('Tom')
dd['dogs'].append('Jack')
print(dd['dogs']) # ['Tom', 'Jack']
print(dd['dogss']) # []
```
## Set 
- A set (Unordered) is an unordered collection of objects that doesn't allow duplicate elements.
- It's very fast (O(1)) for searching operation then a list (O(n)).
>Useful Methods: add(x), pop(), remove(x), clear(), copy(), union(another_set), intersection(another_set), difference(another_set), symmetric_difference(another_set)
> Useful Operators for Set: &, |, -, ^
```python
s = {1,2,3,4}
s.add(5)
print(s) # {1, 2, 3, 4, 5}
```

## Frozenset 
- The frozenset (Unordered & Immutable) class implements an immutable version of set that can't be changed after it's been constructed.
- If we want to create unchangeable set, We can use set.
```python
s = {1,2,3,4}
fs = frozenset(s)
fs.add(5)
print(fs)
# AttributeError: 'frozenset' object has no attribute 'add'
```
# Counter 
Counter (Multiset) is a collection where elements are stored as dictionary keys and their counts are stored as dictionary values. This is useful if you need to keep track of not only if an element is part of a set, but also how may times it's included in the set
>Useful Methods: elements(), most_common([n]), subtract([iterable-or-mapping]), fromkeys(iterable), update([iterable-or-mapping])
```python
from collections import Counter

nums = [2,3,4,3,3,3,4,5]
c_nums = Counter(nums)
print(c_nums)
# Output:  Counter({3: 4, 4: 2, 2: 1, 5: 1})
print(c_nums[3]) # 4
```
## heapq
provides an implementation of the heap queue algorithm, also known as the priority queue algorithm. heapq is a binary heap implementation usually backed by a plain list,  and it supports insertion and extraction of the smallest element in O(log n) time. 
```python
import heapq
heap = [54,65,2,43,5,7]
heapq.heapify(heap)
print(heap[0]) # Output: 2 (Min Item)

heapq.heappush(heap, 50)
print(heap) # [2, 5, 7, 43, 65, 54, 50]

heapq.heappop(heap)
print(heap) # [5, 43, 7, 50, 65, 54]
print(heap[0]) # 5
```








