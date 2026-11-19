# `std::move()`

The `std::move()` function is used to enable the transfer of resources (such as dynamically allocated memory) from one object to another, rather than copying the resources.

It is useful for **transferring ownership** of resources, improving performance and avoiding unnecessary copies.

`std::move()` is defined in the `<utility>` header.

## 1. Move Assignment Operator

Move assignment transfers resources from an existing object to another existing object.

```cpp
#include <iostream>
#include <string>
#include <utility>

int main() {
    std::string from = "Hi this is going to be moved";
    std::string to;

    to = std::move(from);

    // to now owns the transferred resources
}

```

## 2. Move Constructor Operation

```cpp
#include <iostream>
#include <string>
#include <utility>

int main() {
    std::string from = "Hi this is going to be moved";
    

    std::string to = std::move(from);

    // to now owns the transferred resources
}

```