cmake_minimum_required(VERSION 3.12 FATAL_ERROR)

project(replace-resolver VERSION 0.1.0 LANGUAGES CXX)

# [BEGIN] 임시 설정
set(CMAKE_INSTALL_PREFIX "${CMAKE_SOURCE_DIR}/dist")
set(USD_LOCATION "/opt/hfs19.5")
set(USE_HOUDINI_USD ON)
# [END] 임시 설정

list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/defaults)
list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/modules)

include(handleBoostNamespace)

enable_testing()

option(PXR_ENABLE_PYTHON_SUPPORT "Build Python wrapper and Python based tests" ON)

# 임시 설정으로 인해 주석처리
#option(USE_HOUDINI_USD "Build against Houdini USD." OFF)

find_package(USD REQUIRED)

set(USDPLUGIN_NAME replaceResolver)

add_subdirectory(src)

# Install etc folder
install(
  DIRECTORY etc
  DESTINATION .
)
