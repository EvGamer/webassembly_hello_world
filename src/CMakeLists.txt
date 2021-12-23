cmake_minimum_required(VERSION 3.16)

project(wasm_hello_world VERSION 0.0.0)

## Add project source files
file(
	GLOB_RECURSE ALL_SRC
	RELATIVE ${PROJECT_SOURCE_DIR}
	*.cpp *.h
)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})

source_group(TREE ${PROJECT_SOURCE_DIR} FILES ${ALL_SRC})

## Add output
add_executable(${PROJECT_NAME} ${ALL_SRC})


## Copy index file if compile for emscripten
if (EMSCRIPTEN) 
  configure_file(
		${PROJECT_SOURCE_DIR}/wasmAppPage.html
		${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/index.html
		COPYONLY
	)
	set_target_properties(${PROJECT_NAME} PROPERTIES LINK_FLAGS "-s WASM=1 -s EXPORTED_FUNCTIONS='[_main]'")
endif()
