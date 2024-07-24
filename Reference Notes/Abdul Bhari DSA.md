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
	- Code section
	- Stack
	- Heap
- Program is brought from HDD into code section