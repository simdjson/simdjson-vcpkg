# Simple simdjson demo for vcpkg

This project builds a simple executable that
depends on simdjson, under Windows. 

After installing vcpkg and installing
simdjson through it (e.g., `vcpkg install simdjson:x64-windows`), you can build with CMake using a couple of command lines.

You need to pass the location of your `vcpkg/scripts/buildsystems/vcpkg.cmake`  file to CMake:

```
cmake -DCMAKE_TOOLCHAIN_FILE=<location> -B build
cmake --build build
```