# Builder 

We can decompose objects into build steps, this allows us to share the same constructor code between different objects that varify slighty for example from  we can have an electric car, manual car, motorbike , truck.
This would be quite good for complex derivatives using a builder class instead of a factory method as it allows for a variety of different objects to be created.

Good use case if when you have telescoping of variables in a constuctor lets say you have different paramas that need to be configured for a class instead of changing how much you overload them you can use the builder pattern 

This is usually done after a factory method is used. 


# How it works 

Client calls Director that a builder interface. The director has different build steps and the buiilder interface has conceter classes 

Allows for many different configurations that is handled by the director and the builder classes have standardised formats.
```cpp

#include <iostream>
using namespace std;

class Car {
public:
    int speed = 0;
    int horsePower = 0;
    bool turbo = false;
};

class IBuilder {
public:
    virtual void addTurbo() = 0;
    virtual void setHorsePower(int hp) = 0;
    virtual Car getResult() = 0;

    virtual ~IBuilder() = default;
};

class CarBuilder : public IBuilder {
private:
    Car car;

public:
    void addTurbo() override {
        car.turbo = true;
        car.speed = 100;
    }

    void setHorsePower(int hp) override {
        car.horsePower = hp;
    }

    Car getResult() override {
        return car;
    }
};

class Director {
public:
    void makeSportsCar(IBuilder& builder) {
        builder.addTurbo();
        builder.setHorsePower(1000);
    }
};

int main() {
    CarBuilder builder;

    Director director;
    director.makeSportsCar(builder);

    Car car = builder.getResult();

    cout << car.speed << endl;
    cout << car.horsePower << endl;
    cout << car.turbo << endl;
}

```