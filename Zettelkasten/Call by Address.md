2407220925

Status: #idea

Tags: [[Data Structures]] [[Algorithms]] [[C++]]

# Call by Address

```c++
Void changeLength(struct rectangle *p , int l) { 
p -> length = l; } 

int main() { 
struct rectangle r = {10,5}; 
ChangeLength(&r, 20); }

```


---
# References
[[StructAsParameter-19.pdf]]