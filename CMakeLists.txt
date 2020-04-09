cmake_minimum_required(VERSION 3.16)

project(OpenChart)

#------------------------------------------------------------------------------
# Qt
#------------------------------------------------------------------------------
find_package(Qt5 REQUIRED QUIET COMPONENTS Designer)
# find_package(Qt5Gui CONFIG REQUIRED Private)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

#------------------------------------------------------------------------------
# Library
#------------------------------------------------------------------------------
add_library(OpenChart)

#------------------------------------------------------------------------------
# Target
#------------------------------------------------------------------------------
# Define target sources
file(GLOB_RECURSE files ${CMAKE_SOURCE_DIR}/sources/*.cpp ${CMAKE_SOURCE_DIR}/headers/*.h)

target_sources(OpenChart PRIVATE
  ${files}
)

target_link_libraries(OpenChart PUBLIC Qt5::Designer)
target_include_directories(OpenChart PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/headers)

configure_file(
  ${CMAKE_SOURCE_DIR}/CMake/OpenChartConfig.cmake.in
  "${CMAKE_BINARY_DIR}/OpenChartConfig.cmake" @ONLY)

export(TARGETS OpenChart
  FILE "${CMAKE_BINARY_DIR}/OpenChartTargets.cmake")