2407220918

Status: #idea

Tags: [[Data Structures]][[Algorithms]]

# Call by Reference

Call by Reference typically refers to passing a reference (which is often an alias for an alias for 
```c++
int area(struct rectangle &r1) 
{ return r1.length*r1.breath; 
} 

int main() { 
	struct rectangle r = {10,5}; 
	printf("% d", area(r)); 
	}
```



---
# References
[[StructAsParameter-19.pdf]]