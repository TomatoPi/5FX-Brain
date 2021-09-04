cmake_minimum_required(VERSION 3.20.0)
project(5FX-Brain VERSION 0.1.0)

enable_testing()

include(ProcessorCount)
ProcessorCount(N)
if(NOT N EQUAL 0)
  set(CTEST_BUILD_FLAGS -j${N})
  set(ctest_test_args ${ctest_test_args} PARALLEL_LEVEL ${N})
endif()

set(CMAKE_BUILD_TYPE Debug)

set(STD_PERCOMPILED_HEADERS
  <cassert>
  <cstdlib>
  <filesystem>
  <iostream>
  <fstream>
  <string>

  <memory>
  <atomic>
  <tuple>
  <variant>
  <optional>
  <functional>
  
  <vector>
  <map>
  <set>
  <unordered_map>
  <unordered_set>
)

add_subdirectory(5FX-Libs)
add_subdirectory(5FX-Expander)
add_subdirectory(5FX-Autostart)
add_subdirectory(5FX-Session)

add_custom_target(
  ALL
  COMMENT "Run All Tests ... "
  POST_BUILD
  COMMAND make test
)