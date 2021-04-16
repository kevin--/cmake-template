
list( APPEND SOURCE_tests main_test.cpp )

add_executable( cmake-template-test ${SOURCE_tests} )
target_link_libraries(
  cmake-template-test
  PRIVATE
    cmake-template-lib
    Catch2::Catch2
)
