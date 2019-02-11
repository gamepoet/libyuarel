cmake_minimum_required(VERSION 3.8)
project(yuarel VERSION 1.0 LANGUAGES C CXX)

option(YUAREL_BUILD_TESTS "Build tests" OFF)

add_library(
  yuarel
  STATIC
  yuarel.c
  yuarel.h
)
target_include_directories(
  yuarel
  PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  $<INSTALL_INTERFACE:>
)

if (YUAREL_BUILD_TESTS)
  add_executable(
    test_lib
    tests/minunit.h
    tests/test_lib.c
  )
  target_link_libraries(
    test_lib
    yuarel
  )
endif()
