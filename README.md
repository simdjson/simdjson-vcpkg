# Simple simdjson demo for vcpkg
[![Windows-CI](https://github.com/simdjson/simdjson-vcpkg/actions/workflows/ci.yml/badge.svg)](https://github.com/simdjson/simdjson-vcpkg/actions/workflows/ci.yml)

This project builds a simple executable that
depends on simdjson, under Windows. 

After installing vcpkg and installing
simdjson through it (e.g., `vcpkg install simdjson:x64-windows`), you can build with CMake using a couple of command lines.

You need to pass the location of your `vcpkg/scripts/buildsystems/vcpkg.cmake`  file to CMake:

```
cmake -DCMAKE_TOOLCHAIN_FILE=<location> -B build
cmake --build build
```

The CMake will generate and compile the following source file:

```C++
#include "simdjson.h"
#include <iostream>
int main(void) {
    auto cars_json = R"( [
      { "make": "Toyota", "model": "Camry",  "year": 2018, "tire_pressure": [ 40.1, 39.9, 37.7, 40.4 ] },
      { "make": "Kia",    "model": "Soul",   "year": 2012, "tire_pressure": [ 30.1, 31.0, 28.6, 28.7 ] },
      { "make": "Toyota", "model": "Tercel", "year": 1999, "tire_pressure": [ 29.8, 30.0, 30.2, 30.5 ] }
    ] )"_padded;
    std::cout << "parsing : " << cars_json << std::endl;
    simdjson::dom::parser parser;
    simdjson::dom::array obj;
    auto err = parser.parse(cars_json).get(obj);
    if (err) {
      std::cerr << "Failed to parse json" << std::endl;
      std::cerr << err << std::endl;
      return EXIT_FAILURE;
    }
    std::cout << "Success" << std::endl;
    return EXIT_SUCCESS;
}
```

