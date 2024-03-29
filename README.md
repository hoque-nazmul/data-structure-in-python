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
- [Tree Traversals (PreOrder,PostOrder,InOrder)](#tree-traversals-preorderpostorderinorder)
- [Binary Search Tree](#binary-search-tree)
- [Heap](#heap)
- [Heap Sort](#heap-sort)
- [Priority Queue](#priority-queue)
---
# Algorithm
- [Searching Algorithm](#searching-algorith)
    - [Linear Search](#linear-search)
    - [Binary Search](#binary-search)


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
                  (2)
            _______|_______
           |               |
          (7)             (9)
      _____|_____          |_____
     |           |               |
    (1)         (6)             (8)
            _____|_____     _____|_____
           |           |   |           |
          (5)        (10) (3)         (4)
```
- 2 is root node.
- 2 is the parent of 7 & 9. 
- 7 & 9 are the children of 2. They are also sibling of each other.
- 5, 10, 3, 4 are leaf node.
- the defth of (2) is 3 -> 0, 1, 2, 3 (From top to bottom)
- the height of (4) is also 3 -> 0, 1, 2, 3 (From bottom to top)
- the path of 5 is 5, 6, 7, 2
- the level of 7,9 is 1 -> it's start from 0 like defth & height
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
> If we want to record the parent node, we have to do like that. (We can skip this primarily)
```python
class TreeNode:
    def __init__(self, data):
        self.data = data  
        self.parent = None
        self.left = None 
        self.right = None 

    def __repr__(self):
        return repr(self.data)

    def add_left(self, node):
        self.left = node 
        if node is not None:
            node.parent = self

    def add_right(self, node):
        self.right = node 
        if node is not None:
            node.parent = self
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Tree Traversals (PreOrder,PostOrder,InOrder)
```python
                  (2)
            _______|_______
           |               |
          (7)             (9)
      _____|_____          |_____
     |           |               |
    (1)         (6)             (8)
            _____|_____     _____|_____
           |           |   |           |
          (5)        (10) (3)         (4)
```
#### Pre-Order
>First->root_node, then->left_node, then->right_node
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
>First->left_node, then->right_node, then->root_node
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
>First->left_node, then->root_node, then->right_node
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
**[⬆ back to top](#Data-Structure-in-Python)**

## Binary Search Tree
```python
class TreeNode:
    def __init__(self, data):
        self.data = data 
        self.parent = None 
        self.left = None 
        self.right = None 

    def __repr__(self):
        return repr(self.data) 

    def add_left(self, node):
        self.left = node 
        if node is not None:
            node.parent = self 

    def add_right(self, node):
        self.right = node 
        if node is not None:
            node.parent = self 
            

def bst_insert(root, node):
    last_node = None 
    current_node = root 

    while current_node is not None: 
        last_node = current_node 
        if node.data < current_node.data:
            current_node = current_node.left 
        else:
            current_node = current_node.right 

    if last_node is None:
        root = node 
    elif node.data < last_node.data:
        last_node.add_left(node)
    else:
        last_node.add_right(node)

    return root 


def bst_create():
    root = TreeNode(10)

    for item in [5,17,3,7,12,19,1,4]:
        node = TreeNode(item)
        root = bst_insert(root, node)

    return root 

def in_order(node):
    if node.left:
        in_order(node.left)
    print(node)
    if node.right:
        in_order(node.right)


def bst_search(node, key):
    while node is not None:
        if node.data == key:
            return node 
        if key < node.data:
            node = node.left 
        else: 
            node = node.right 

        return node 


def bst_minimum(root):
    while root.left is not None:
        root = root.left 

    return root 


def bst_transplant(root, current_node, new_node):
    if current_node.parent is None:
        root = new_node 
    elif current_node == current_node.parent.left:
        current_node.parent.add_left(new_node)
    else:
        current_node.parent.add_right(new_node)

    return root 


def bst_delete(root, node):
    if node.left is None:
        root = bst_transplant(root, node, node.right)
    elif node.right is None:
        root = bst_transplant(root, node, node.left)
    else: 
        min_node = bst_minimum(node.right)
        if min_node.parent != node:
            root = bst_transplant(root, min_node, min_node.right)
            min_node.add_right(node.right)
        root = bst_transplant(root, node, min_node)
        min_node.add_left(node.left)

    return root 


if __name__ == "__main__":
    root = bst_create()
    print("BST")
    in_order(root)

    for key in [1,5,10]:
        node = bst_search(root, key)
        root = bst_delete(root, node)
        print("BST")
        in_order(root)
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Heap
```python
heap = [None] * 10 

heap[1] = 19 
heap[1*2] = 7
heap[1*2+1] = 17

heap[2 * 2] = 3
heap[2*2+1] = 5

heap[3 * 2] = 12
heap[3 * 2 + 1] = 10 

heap[4 * 2] = 1 
heap[4 * 2 + 1] = 2

# Find the left, right, parent index
def left(i):
    return i * 2 
def right(i):
    return i * 2 + 1 
def parent(i):
    return i // 2 


def is_max_heap(heap):
    n = len(heap) - 1
    for i in range(n, 1, -1):
        p = parent(i)

        if heap[p] < heap[i]:
            return False 

    return True


def max_heapify(heap, heap_size, i):
    left_child = left(i)
    right_child = right(i)

    if left_child <= heap_size and heap[left_child] > heap[i]:
        largest = left_child 
    else:
        largest = i 

    if right_child <= heap_size and heap[right_child] > heap[largest]:
        largest = right_child 

    if largest != i:
        heap[i], heap[largest] = heap[largest], heap[i]
        max_heapify(heap, heap_size, largest)


def build_max_heap(heap):
    heap_size = len(heap) - 1

    for i in range(heap_size // 2, 0, -1):
        max_heapify(heap, heap_size, i)


if __name__ == "__main__":
    print(heap)
    build_max_heap(heap)
    print(heap)
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Heap Sort
```python
def heap_sort(heap):
    build_max_heap(heap)
    heap_size = len(heap) - 1

    for i in range(heap_size, 1, -1):
        heap[1], heap[i] = heap[i], heap[1]
        heap_size -= 1
        max_heapify(heap, heap_size, 1)

if __name__ == "__main__":
    heap = [None, 12, 7, 1, 3, 10, 17, 19, 2, 5]
    heap_sort(heap)
    print(heap)
    # Output: [None, 1, 2, 3, 5, 7, 10, 12, 17, 19]
```
**[⬆ back to top](#Data-Structure-in-Python)**

## Priority Queue
```python
def get_maximum(heap):
    heap_size = len(heap) - 1
    max_item = heap[1]

    heap[1] = heap[heap_size]
    heap_size -= 1 

    max_heapify(heap, heap_size, 1)

    return max_item    


def insert_node(heap, heap_size, node):
    heap_size += 1
    heap[heap_size] = node

    i = heap_size
    while i > 1 and heap[i] > heap[parent(i)]:
        heap[parent(i)], heap[i] = heap[i], heap[parent(i)]
        i = parent(i) 

    return heap_size

if __name__ == "__main__":
    heap = [None,19,7,17,3,5,12,10,1,2]

    # Get the Max Priority Value
    print(get_maximum(heap)) # Output: 19
    print(heap) # Output: [None, 17, 7, 12, 3, 5, 2, 10, 1, 2]

    # Insertion
    insert_node(heap, 8, 100)
    print(heap) # Output [None, 100, 17, 12, 7, 5, 2, 10, 1, 3]

    # Insertion
    insert_node(heap, 8, 100)
    print(heap) # Output [None, 100, 17, 12, 7, 5, 2, 10, 1, 3]
```
**[⬆ back to top](#Data-Structure-in-Python)**


# Searching Algorithm
## Linear Search
```python
nums = [44, 32, 64, 75, 43, 54, 76]

def linear_search(nums, x):
    length = len(nums)
    for i in range(length):
        if nums[i] == x:
            return i 
    return -1 

print(linear_search(nums, 43)) # Output: 4
print(linear_search(nums, 100)) # Output: -1
```
## Binary Search
```python
li = [21, 23, 25, 34, 37, 38, 40, 45, 49, 50, 55, 58, 60]

def binary_search(nums, x):
    left = 0
    right = len(nums) - 1 

    while left <= right:
        mid = (left + right) // 2 

        if nums[mid] == x:
            return mid 

        if nums[mid] < x: 
            left = mid + 1
        else:
            right = mid - 1 
        
    return -1 

print(binary_search(li, 25)) # Output: 2
print(binary_search(li, 100)) # Output: -1
```
**[⬆ back to top](#Data-Structure-in-Python)**

