# Singleton Pattern

Use this when you want to enforce creation of an object only once. Example use case is a logger, database connection managers , config managers.

```cpp
class Single {
private:
    // Disable copy and move
    Single() = default;

    Single(const Single&) = delete; //need const so it can also take in const objects as well as non const 
    Single(Single&&) = delete;      //do not need const as the move const/allocator alters the object taken in 

    Single& operator=(const Single&) = delete;
    Single& operator=(Single&&) = delete;

public:
    static Single& getInstance() {      //static means that this function is shared between all instances of the object 
        static Single instance;  
        return instance;
    }
};

int main() {
    // Get the singleton instance
    Single& s1 = Single::getInstance();
    Single& s2 = Single::getInstance();

    return 0;
}

```
