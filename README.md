<div align="center"> 
    <img src="assets/logo.svg" height=312>
</div>

<br/>

<p align="center">
  A C++20 library that provides (opt-in) bit-wise operations for arbitrary `enum class`es
</p>

</div>

## 📦 Installation

* Using [CPM](https://github.com/cpm-cmake/CPM.cmake)
  ```cmake
  CPMFindPackage(
    NAME           flagpp
    VERSION        2.0
    GIT_REPOSITORY "https://github.com/Curve/flagpp"
  )
  ```

* Using FetchContent
  ```cmake
  include(FetchContent)

  FetchContent_Declare(flagpp GIT_REPOSITORY "https://github.com/Curve/flagpp" GIT_TAG v2.0)
  FetchContent_MakeAvailable(flagpp)

  target_link_libraries(<target> flagpp)
  ```

## 📃 Usage

```cpp
#include <flagpp/flags.hpp>

enum class my_enum
{
    none,
    a = 1 << 0,
    b = 1 << 1,
    c = 1 << 2,
};

template <>
constexpr bool flagpp::enabled<my_enum> = true;

// You can now use `my_enum` for bit-wise operations!

auto flag = my_enum::a;
flag |= my_enum::b;
flag |= my_enum::c;

if (flag & my_enum::b)
{
    flag &= ~my_enum::b;
}
```

> For more examples see [tests](tests/)
