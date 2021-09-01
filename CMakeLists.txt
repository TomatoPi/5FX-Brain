cmake_minimum_required(VERSION 3.20.0)
project(5FX-Brain VERSION 0.1.0)

enable_testing()

set(STD_PERCOMPILED_HEADERS
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