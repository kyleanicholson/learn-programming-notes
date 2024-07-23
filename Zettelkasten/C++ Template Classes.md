2407230918

Status: #idea

Tags: [[C++]] [[Object-Oriented Programming]]

# C++ Template Classes

**Templates** in C++ allow you to write generic and reusable code. A **template class** is a blueprint for creating classes or functions to handle any data type without rewriting code for each type.

#### When to Use Template Classes

- **Code Reusability:** Avoid duplicating code for different data types.
- **Type Safety:** Ensures type checking at compile time.
- **Flexibility:** Works with any data type, making your code more flexible.

```c++
#include <iostream>
using namespace std;

// Template class definition
template <typename T1, typename T2>
class Pair {
private:
    T1 first;
    T2 second;

public:
    Pair(T1 first, T2 second) : first(first), second(second) {}

    T1 getFirst() const {
        return first;
    }

    T2 getSecond() const {
        return second;
    }

    void setFirst(T1 value) {
        first = value;
    }

    void setSecond(T2 value) {
        second = value;
    }

    void print() const {
        cout << "Pair(" << first << ", " << second << ")" << endl;
    }
};

int main() {
    // Creating a Pair of int and double
    Pair<int, double> p1(10, 15.5);
    p1.print();

    // Creating a Pair of string and char
    Pair<string, char> p2("Hello", 'A');
    p2.print();

    return 0;
}

```
---
# References

Abdul Bari Algorithms Udemy S1 #29
https://www.udemy.com/course/datastructurescncpp/learn/lecture/13612176#overview