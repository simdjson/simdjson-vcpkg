# Simple simdjson demo for vcpkg

Usage after installing vcpkg and installing
simdjson through it.

You need the location of your `vcpkg/scripts/buildsystems/vcpkg.cmake` file:

```
cmake -DCMAKE_TOOLCHAIN_FILE=<location> -B build
cmake --build build
```