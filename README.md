# Data-Structure-in-Python

- [List](#list)
- [Deque](#deque)
- [Tuple](#tuple)
- [Dictionary](#dictionary)
- [Default Dictionary](#default-dictionary)
- [Set](#set)
- [Frozenset](#frozenset)
- [Counter](#counter)
- [heapq](#heapq)
---
- [Doubly Linked List](#doubly-linked-list)
- [Stack](#stack)
- [Queue](#queue)
- [Tree](#tree)
- [Tree Traversals (PreOrder,PostOrder,InOrder)](#tree-traversals(preorder,postorder,inorder))

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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**
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
**[⬆ back to top](#Data-Structure-in-Python)**


## Doubly Linked List
```python
class Node:
    def __init__(self, value):
        self.prev = None
        self.next = None
        self.val = value

class DoubleLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None
        self.size = 0

    def add(self, val):
        node = Node(val)

        if self.tail is None:
            self.head = node 
            self.tail = node 
            self.size += 1
        else:
            self.tail.next = node 
            node.prev = self.tail
            self.tail = node 
            self.size += 1

    def __remove_val(self, node):
        if node.prev is None: 
            self.head = node.next
        else:
            node.prev.next = node.next

        if node.next is None:
            self.tail = node.prev 
        else:
            node.next.prev = node.prev

        self.size -= 1

    def remove (self, value):
        node = self.head 
        while node is not None:
            if node.val == value:
                self.__remove_val(node)
                break

            node = node.next

    def remove_first(self):
        if self.head is not None:
            self.__remove_val(self.head)

    def remove_last(self):
        if self.tail is not None:
            self.__remove_val(self.tail)

    # LinkedList Representation
    def __str__(self):
        vals = []
        node = self.head 
        while node is not None:
            vals.append(node.val)
            node = node.next 
            
        return f"[{', '.join(str(val) for val in vals)}]"
    
dbl = DoubleLinkedList()
dbl.add(2)
dbl.add(5)
dbl.add(10)
dbl.add(10)
dbl.add(10)
dbl.add(15)
print(dbl) # [2, 5, 10, 10, 10, 15]

dbl.remove_first()
print(dbl) # [5, 10, 10, 10, 15]

dbl.remove_last()
print(dbl) # [5, 10, 10, 10]

dbl.remove(10)
print(dbl) # [5, 10, 10]

print(dbl.size) # 3
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Stack 
>Implementing Stack Using Linked List
```python 
from linked_list import DoubleLinkedList

class Stack:
    def __init__(self):
        self.__list = DoubleLinkedList()

    def is_empty(self):
        return self.__list.size == 0

    def push(self, val):
        self.__list.add(val)

    def pop(self):
        if self.is_empty() is not True:
            last_item = self.__list.back()
            self.__list.remove_last() 
            return last_item

    def peek(self):
        if self.is_empty() is not True: 
            return self.__list.back()

    def __len__(self):
        return self.__list.size


st = Stack()
print(st.is_empty()) # True
st.push(43) 
st.push(40)
st.push(90)
print(len(st)) # 3
print(st.pop()) # 90
print(len(st)) # 2
print(st.peek()) # 40
```
>Implementing Stack using Python List
```python 
class Stack:
    def __init__(self):
        self.__list = []
    
    def is_empty(self):
        return len(self.__list) == 0

    def push(self, val):
        self.__list.append(val)

    def pop(self):
        return self.__list.pop()

    def peek(self):
        return self.__list[-1]

    def get_stack(self):
        return self.__list

st = Stack()
st.push(32)
st.push(20)
print(st.get_stack()) # [32, 20]
print(st.pop()) # 20
print(st.peek()) # 32
print(st.get_stack()) # [32]
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Queue
>Implementing Queue using Linked List 
```python
from linked_list import DoubleLinkedList 

class Queue:
    def __init__(self):
        self.__list = DoubleLinkedList()

    def is_empty(self):
        return self.__list.size == 0 

    def enqueue(self, val):
        self.__list.add(val)

    def dequeue(self):
        if self.is_empty() is not True:
            first_item = self.__list.front()
            self.__list.remove_first() 
            return first_item 

    def front(self):
        if self.is_empty() is not True: 
            return self.__list.front()

    def __len__(self):
        return self.__list.size

qu = Queue() 
qu.enqueue(32)
qu.enqueue(53)
print(qu.front()) #32
print(len(qu)) # 2
print(qu.dequeue()) # 32 
print(qu.front()) # 53
print(len(qu)) # 1
```
>Implementing Queue using Python List
```python 
class Queue:
    def __init__(self):
        self.__list = [] 

    def is_empty(self):
        return len(self.__list) == 0 

    def enqueue(self, val):
        self.__list.append(val)

    def dequeue(self):
        if self.is_empty() is not True: 
            return self.__list.pop(0)

    def front(self):
        if self.is_empty() is not True:
            return self.__list[0]

    def __len__(self):
        return len(self.__list)

qu = Queue() 
qu.enqueue(32)
qu.enqueue(53)
print(qu.front()) #32
print(len(qu)) # 2
print(qu.dequeue()) # 32 
print(qu.front()) # 53
print(len(qu)) # 1
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Tree
```python
class TreeNode:
    def __init__(self, data):
        self.data = data  
        self.left = None 
        self.right = None 

    def __repr__(self):
        return repr(self.data)

    def add_left(self, node):
        self.left = node 

    def add_right(self, node):
        self.right = node 

def create_tree():
    two = TreeNode(2)
    seven = TreeNode(7)
    nine = TreeNode(9)
    two.add_left(seven)
    two.add_right(nine)

    one = TreeNode(1)
    six = TreeNode(6)
    seven.add_left(one)
    seven.add_right(six)

    five = TreeNode(5)
    ten = TreeNode(10)
    six.add_left(five)
    six.add_right(ten)

    eight = TreeNode(8)
    nine.add_right(eight)

    three = TreeNode(3)
    four = TreeNode(4)
    eight.add_left(three)
    eight.add_right(four)

    return two 
```
## Tree Traversals (PreOrder,PostOrder,InOrder)
#### Pre-Order
```python
from binary_tree import create_tree

def pre_order(node):
    print(node, end=", ")

    if node.left:
        pre_order(node.left)

    if node.right:
        pre_order(node.right)


if __name__ == '__main__':
    root = create_tree()
    pre_order(root)

# Output: 2, 7, 1, 6, 5, 10, 9, 8, 3, 4
```
#### Post-Order
```python
from binary_tree import create_tree

def post_order(node):
    if node.left:
        post_order(node.left)

    if node.right:
        post_order(node.right)

    print(node, end=', ')


if __name__ == '__main__':
    root = create_tree()
    post_order(root)

# Output: 1, 5, 10, 6, 7, 3, 4, 8, 9, 2
```
#### In-Order
```python
from binary_tree import create_tree

def in_order(node):
    if node.left:
        in_order(node.left)

    print(node, end=", ")

    if node.right:
        in_order(node.right)

if __name__ == '__main__':
    root = create_tree()
    in_order(root)

# Output: 1, 7, 5, 6, 10, 2, 9, 3, 8, 4
```