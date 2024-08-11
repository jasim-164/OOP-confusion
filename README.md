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
