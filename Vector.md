# Vector 

Container that stores memory in a contigously, next to each other. 

When a vector is full and push_back method is used :

compared to 
In gcc compiler it doubles the vectors size or increases it by the amout of values put in if thats larger than double
But according to the iso this is no strict, just that it allocates more memory.
```cpp

      push_back(const value_type& __x)
      {
        if (this->_M_impl._M_finish != this->_M_impl._M_end_of_storage)
          {
            _GLIBCXX_ASAN_ANNOTATE_GROW(1);
            _Alloc_traits::construct(this->_M_impl, this->_M_impl._M_finish,
                                     __x);
            ++this->_M_impl._M_finish;
            _GLIBCXX_ASAN_ANNOTATE_GREW(1);
          }
        else
          _M_realloc_append(__x);
      }
```

Need to have a good understanding of design patterns and how to implement them 
As well as an overview of software archetecture