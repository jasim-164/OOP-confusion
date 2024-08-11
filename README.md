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
