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

## List (Mutable)
- Python's list are implemented as dynamic arrays behind the scenes.
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
## Tuple (Immutable)
- If we want to store no-changeable data, tuple is a good choice for that.
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









