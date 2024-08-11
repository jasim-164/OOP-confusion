# OOP-confusion
## Problem-1: Abstract class e object create korle error dibe. jekhane pure virtual function declare thakbe setai abstract class.
```#include <iostream>
using namespace std;

class Animal {
public:
    virtual void speak()=0;
};

class Cat : public Animal {
public:
    void speak() override {
        cout << "Cat meows";
    }
};
int main()
{
    Animal obj;//error
    obj.speak();
}
```
# Problem-2: shallow copy Vs deep copy
## Problem with Shallow Copy:
### When obj2 modifies the data, obj1 is also affected because both objects share the same memory location. If either object is destroyed, the other object is left with a dangling pointer.

# Benefit of Deep Copy:
In this example, obj1 and obj2 have their own separate copies of the data. Changes to obj2 do not affect obj1, and each object manages its own memory, preventing issues like double deletion.


## Problem-3: How destructor and constructor is called
```
#include <iostream>
using namespace std;

class mycls1 {
    private:
    int x;
    int i=0;
public:
    mycls1()
    {
        cout<<"default constructor created"<<endl;
    }
    mycls1(int p)
    {
        x=p;
        cout<<"parameterized constructor created"<<endl;
        cout<<x<<endl;
    }
    mycls1(mycls1 & copy)
    {
        x=copy.x;
        cout<<"copy constructor is called"<<endl;
        cout<<x<<endl;
        
    }
    
    ~ mycls1()
    {
         i++;
         cout<<"destructor is called "<<i <<" "<<x <<endl;
    }
};


int main()
{
   mycls1 obj;
   mycls1 obj1(10);
   mycls1 obj2(obj1);
   
}
```
```
Your Output
default constructor created
parameterized constructor created
10
copy constructor is called
10
destructor is called 1 10
destructor is called 1 10
destructor is called 1 0
```
# Problem-4: friend function
A friend function in C++ is a function that is not a member of a class but has access to the class's private and protected members. This function is declared with the friend keyword inside the class whose members it needs to access.

Key Characteristics of Friend Functions:
Access to Private and Protected Members: A friend function can access private and protected data members of the class it is declared as a friend of, which regular non-member functions cannot do.

Not a Member Function: Even though a friend function has access to private and protected members, it is not considered a member of the class. This means it is not called using an object of the class and does not have a this pointer.

Declared Inside the Class: The friend function is declared inside the class using the friend keyword. However, the definition (implementation) of the function can be outside the class.

When to Use a Friend Function:
When you need to perform operations that involve private data members of two or more classes.
When you need a function to access private members but do not want it to be a member of the class.

```
#include <iostream>
using namespace std;

class MyClass {
private:
    int x;
    int y;

public:
    MyClass(int a, int b) : x(a), y(b) {}

    // Friend function declaration
    friend int sum(MyClass obj);
};

// Friend function definition
int sum(MyClass obj) {
    return obj.x + obj.y; // Access private members x and y
}

int main() {
    MyClass obj(10, 20);

    // Call the friend function
    cout << "Sum: " << sum(obj) << endl;

    return 0;
}

```
