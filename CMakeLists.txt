# CMakeLists.txt (delta)
# Copyright (c) 2015, Moritz Pflanzer}
# Imperial College London. All rights reserved.

cmake_minimum_required(VERSION 2.8.12)
project(delta)

find_package(FLEX)
include_directories(${PROJECT_BINARY_DIR})

FLEX_TARGET(topformflat_scanner topformflat.lex ${PROJECT_BINARY_DIR}/topformflat.c)

add_executable(topformflat
  ${FLEX_topformflat_scanner_OUTPUTS}
)

install(TARGETS topformflat
  RUNTIME DESTINATION "${CMAKE_INSTALL_PREFIX}"
)

install(PROGRAMS
  "delta"
  "multidelta"
  DESTINATION "${CMAKE_INSTALL_PREFIX}"
)