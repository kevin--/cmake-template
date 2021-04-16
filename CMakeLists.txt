cmake_minimum_required( VERSION 3.12 )

project( cmake-template LANGUAGES CXX )

set( CMAKE_CXX_STANDARD          17  ) 
set( CMAKE_CXX_STANDARD_REQUIRED ON  )
set( CMAKE_CXX_EXTENSIONS        OFF )

### turn on this on to build the tests
option( BUILD_TESTS OFF )

### Library

list(APPEND FILES_source src/Class.cpp )

add_library( cmake-template-lib ${FILES_source} )
target_include_directories(
  cmake-template-lib
  PUBLIC
    include
  PRIVATE
    src
)

### Executable

list(APPEND FILES_main src/main.cpp )

add_executable( cmake-template ${FILES_main} )
target_link_libraries( cmake-template PRIVATE cmake-template-lib )

### Tests

if ( BUILD_TESTS )
  add_subdirectory( lib/Catch2 )
  add_subdirectory( test )
endif()
