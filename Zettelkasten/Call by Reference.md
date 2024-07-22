2407220918

Status: #idea

Tags: [[Data Structures]][[Algorithms]]

# Call by Reference

 Using call by reference, the structure that is passed to the function is modified by the function - the parameters themselves are modified instead of a copy being modified.
```c++
int area(struct rectangle &r1) 
{ return r1.length*r1.breath; 
} 

int main() { 
	struct rectangle r = {10,5}; 
	printf("% d", area(r)); 
	}
```

Here the new object is not created but the same object is called r1 also. Thus new changes in the values will effect the actual parameters.

---
# References
