cmake_minimum_required(VERSION 3.0)

add_compile_options(
  -Wall
  -Wextra
  -Wpedantic
  -pie
  -fpie
  -O3
)

project(simple)

add_executable (
  hello2.temp.binary
  hello2.cpp
)

add_custom_command(
  OUTPUT final.solution
  COMMAND upx hello2.temp.binary -o hello2.x86_64.compressed.dynamic.binary
  COMMENT "OMG"
  VERBATIM
)

add_custom_target(
  Last_Target ALL
  DEPENDS final.solution
)
