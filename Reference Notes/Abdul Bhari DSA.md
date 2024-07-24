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

c uses `malloc` instead of new.
## 42. Types of Data Structures

- 