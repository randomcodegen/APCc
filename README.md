# APCc

A C port of [APCpp](https://github.com/N00byKing/APCpp) for Archipelago clients.

## Build

Requires CMake 3.24+, GLib, Jansson, OpenSSL and zlib. 
Install those dependencies with your package manager. 
The included recipe builds a pinned, unpatched
libwebsockets version with compression enabled and the connection fixes included.

Compile `APCc.c` into your client, link GLib and Jansson, and add:

```cmake
add_subdirectory("${APCC_ROOT}/cmake/libwebsockets"
                 "${CMAKE_CURRENT_BINARY_DIR}/apcc-libwebsockets")
target_link_libraries(your_client PRIVATE websockets)
```

The target provides libwebsockets and its dependencies. 
In vcpkg manifests, replace `libwebsockets` with `openssl` and `zlib`. 
Rebuild the client after updating APCc.

### Native Visual Studio projects

Build and install libwebsockets separately:

```powershell
cmake -S C:/path/to/APCc/cmake/libwebsockets -B build-lws -A x64 -DCMAKE_TOOLCHAIN_FILE=C:/path/to/vcpkg/scripts/buildsystems/vcpkg.cmake -DVCPKG_MANIFEST_MODE=OFF
cmake --build build-lws --config Release --target websockets
cmake --install build-lws --config Release --prefix C:/path/to/lws-install
```

Use the installed headers and `websockets_static.lib`, plus OpenSSL, zlib and Windows system libraries. 

## License

LGPL-2.1-only; see [LICENSE](LICENSE). Based on APCpp by N00byKing and contributors.
C port and modifications copyright (c) 2024-2026 randomcodegen.

When distributing binaries, include license notices, corresponding library sources and build scripts, and the materials required to relink modified libraries under LGPL 2.1. Dependencies retain their own licenses.
