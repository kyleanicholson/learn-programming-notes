2407220925

Status: #idea

Tags: [[Data Structures]] [[Algorithms]] [[C++]]

# Call by Address

Call by address involves passing the address (memory address) of a variable (a pointer) to a function. The function then can use the pointer to modify the original variable. This is a common practice in C.

```c++
Void changeLength(struct rectangle *p , int l) { 
p -> length = l; 
} 

int main() { 
struct rectangle r = {10,5}; 
ChangeLength(&r, 20); }

```


---
# References
[[StructAsParameter-19.pdf]]