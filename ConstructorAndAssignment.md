# Constructor and Assignment operations

Constructor operator is when an object is being created, this triggers the copy or move constructor

```cpp
class Example{
public : 
    Example(&&int) // Move constructor
    Example(int);   // Copy constructor
};

int main(){
    Example(10);    //Move constructor used
    int a = 10;
    Example(a);     //copy constructor used 
}
```

Assigment are when we already initilize the object and then give the object a value 
We return a derefenced pointer from the object 

```cpp
class Example {
public:

    // Copy assignment operator
    Example& operator=(const Example& other) {
        return *this;
    }

    // Move assignment operator
    Example& operator=(Example&& other) {
        return *this;
    }
};
```