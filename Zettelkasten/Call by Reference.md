2407220918

Status: #idea

Tags: [[Data Structures]][[Algorithms]]

# Call by Reference

Call by Reference typically refers to passing a reference (whi)
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
[[StructAsParameter-19.pdf]]