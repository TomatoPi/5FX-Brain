cmake_minimum_required(VERSION 3.20.0)
project(5FX-Brain VERSION 0.2.0)

enable_testing()

include(ProcessorCount)
ProcessorCount(N)
if(NOT N EQUAL 0)
  set(CTEST_BUILD_FLAGS -j${N})
  set(ctest_test_args ${ctest_test_args} PARALLEL_LEVEL ${N})
endif()

add_subdirectory(5FX-Tools)
add_subdirectory(5FX-Syncer)

add_custom_target(
  ALL
  COMMENT "Run All Tests ... "
  POST_BUILD
  COMMAND ${CMAKE_MAKE_PROGRAM} test
)