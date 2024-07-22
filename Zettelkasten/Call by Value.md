2407220905

Status: #idea

Tags: [[Data Structures]] [[Algorithms]] [[C++]]

# Call by Value

When a function uses call by value, when the function is called, a separate object will be created in the function call and everything will be copied into that object. 

The object that is passed is not modified directly by the function, as is the case with call by reference 

call by value - Example 
```c++
int area(struct rectangle r1) { return r1.length*r1.breath; } int main() {
struct rectangle r = {10,5}; printf("% d", area(r)); }
```



---
# References
