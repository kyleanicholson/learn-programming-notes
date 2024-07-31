# Abdul Bhari DSA

Reference Link: https://www.udemy.com/course/datastructurescncpp/learn
Reference Type: Course

*Note I don't have notes here for the first section which covers C++ and C*
## 39. Introduction - Data Structures, Databases, Data Warehouses

- **Data Structure**: Arrangement of collection of data items so that operations on that data can be done efficiently.
- Where do data structures live? 
	- Main memory (RAM)
	- Applications can use data structures for arranging their data.
- When a program (stored on HD) is run, it is brought into main memory. Then the CPU executes that program. 
- Data is also brought into the main memory (for example a MS Word document) -- cannot be processed when in the hard drive.
- **Database**: Storage for large amounts of data that is organized in tables (often relational tables) on the hard drive. 
	- Application programs access the database, which is pulled into main memory by applications and stored in the form of data structures.
-**Data Warehouse**: Very large sized "big data" that may not be used daily - historical data -- can be accessed as required. Often stored across multiple hard drives.

## 40. Stack vs Heap Memory

- Each byte of main memory has an address (single value)
- Larger RAM is divided into segments (often 64kb)
- Memory segment is divided into 
	- Code section (machine code copied from HD)
	- Stack
	- Heap
- Program code is brought from HDD into code section
	- CPU starts executing
- Static memory allocation: Memory for variables declared inside program is allocated in the stack at compile time
	- This memory is known as the 'stack frame' or 'activation record' of the function

## 41. Stack vs Heap contd.

- When functions are called, activation records are allocated in the stack. The active function is at the topmost layer of the stack.
- When the function has finished executing its last statement, that function's activation record is removed from the stack.
- Stack memory behaves like a 'stack' of functions -- it is 'organized memory'

- Heap refers to unorganized memory - must be treated like a resource -- when required you use the memory, when not required you must release (free) the memory.
- Programs cannot directly access heap memory-- memory is accessed and allocated using pointers.

```c++
void main(){
	int *p; // Allocated in stack - used to access the heap values
	p = new int[5]; // Allocated in heap
	delete [p] // Deallocates the memory
}
```

c uses `malloc` instead of new to assign memory in heap.
## 42. Types of Data Structures

- Physical Data Structures (defines how memory is organized / allocated)
	- Array: Collection of contiguous memory locations (fixed size)
		- Can be created in stack of heap (using pointer)
		- Should be used when you know the maximum length of the list
	- Linked List: Collection of nodes where each node contains data and a link to the next node.
		- Always created in heap
		- Can have variable length - use when you don't know the size of the list
- Logical Data Structures (implemented using physical data structures)
	- Stack (linear): LIFO - Last in First Out
	- Queue (linear): FIFO - First in First Out
	- Tree (nonlinear)
	- Graph (nonlinear)
	- Hash Table (tabular)

## 43. Abstract Data Type (ADT)

- Representation of data
- Operation on data
- Integers 
	- Represented by 16 bits (2 bytes)
	- Operations are + / - * % ++ --
- OOP - can define our own abstract data types
- How to represent a List?
	- Data:  
		- 1 - space for storing elements
		- 2 - capacity
		- 3 - size
	- Operations
		- Add/append(element): Add to the end of the list 
		- Insert(idx, ele): Add an element at a given index
		- Remove(idx) 
		- Set(index, element): Replace an element at a given index
		- Get(index): Get the element at index
		- Search(key)/contains(key): Search for an element to find its index 
		- Sort(): Arrange in order
- Abstract means you don't need to know the inner workings to use the data structure - the data and operations are hidden within the class's implementation.

## 44.  Time and Space Complexity

- Time Complexity: How much time a machine takes -- depends on the procedure you are doing.
	- Array operations - list of elements 'n' -- we don't know how many elements
		- O(n): If you go through each element once (adding or searching)
		- O(n^2): If you compare each element to every other element
			- Nested for loop means it's n^2
		- O(log n): When something is successively divided until it reaches 1
			- For example, in a for loop the counter variable gets divided by 2
	- Matrix Operations
		- O(n^2): If you process all the elements
		- O(n): If you only process a row or column
	- Binary Tree
		- 