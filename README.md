# out_param
A template for declaring function's output parameters

## Motivation

This small class template `out_param` can be used to indicate in the function's signature that a given reference parameter is an *output parameter*:

```c++
using namespace ak_toolkit;

void assign(out_param<std::string&> s, // < output parameter
            std::string const& v)
{
    s.get() = v;
}
```

It does not do any processing. The only benefit of using it is that you cannot pass a reference to a function unless you explicitly wrap it:

```c++
std::string s;
assign(out(s), "text");
```

This forces the function callers to be explicit about passing output arguments to it.

## Recommendation
Before using this library for output parameters consider not using output parameters at all, as described in C++ Core Guidelines [F.20](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rf-out) and [F.21](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rf-out-multi). Only if this is impossible resort to using this library to make the usage of output parameters explicit in the call site.

## installation
It is a C++11 single-header (header-only) library.

## License
Distributed under the [Boost Software License, Version 1.0](http://www.boost.org/LICENSE_1_0.txt).
