## Hello World for Emscripten

### Configure cmake for emscripten
- Install [emscripten SDK](https://emscripten.org/docs/getting_started/downloads.html)
- Select "specify toolchain file for cross-compiling"
- In emscripten SDK directory select toolchain file at `./upstream/emscripten/cmake/Modules/Platform/Emscripten.cmake` 
- As NODE_JS_EXECUTABLE set `$path_to_emsdk/node/$node_version/bin/node` where you substitute `$path_to_emsdk` with path to emscripten SDK
 and `$node_version` with node version that is available there

### Build
- Configure Cmake
- Run `make` in the build directory