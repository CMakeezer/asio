cmake_minimum_required(VERSION 3.0)

project(asio)

set(CMAKE_CXX_STANDARD 14)

option(BUILD_EXAMPLES "Build internal examples" ON)

option(ENABLE_CXX_11_EXAMPLES "Build internal C++11 examples" ON)
option(ENABLE_CXX_14_EXAMPLES "Build internal C++14 examples" OFF)
option(ENABLE_CXX_17_EXAMPLES "Build internal C++17 examples" OFF)


add_library(asio STATIC
  ${CMAKE_CURRENT_LIST_DIR}/asio/src/asio.cpp
  ${CMAKE_CURRENT_LIST_DIR}/asio/src/asio_ssl.cpp)

target_include_directories(asio
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/asio/include>
    $<INSTALL_INTERFACE:include>)

target_compile_definitions(asio
  PRIVATE
    -DASIO_STANDALONE=1
    -DASIO_SEPARATE_COMPILATION=1
    -DASIO_NO_TYPEID=1)

if(WIN32)
target_compile_definitions(asio
  PRIVATE
    -D_WIN32_WINNT=0x0501)
endif()

target_compile_features(asio
  PUBLIC
    cxx_alias_templates
    cxx_auto_type
    cxx_decltype
    cxx_final
    cxx_lambdas
    cxx_variadic_templates
    cxx_defaulted_functions
    cxx_nullptr)

if(BUILD_EXAMPLES)
  set(EXAMPLE_PATH ${CMAKE_CURRENT_LIST_DIR}/asio/src/examples)
  add_subdirectory(asio/src/examples)
endif()

install(
        TARGETS asio
        EXPORT asio-cmake
        ARCHIVE DESTINATION lib/
        LIBRARY DESTINATION lib/
        RUNTIME DESTINATION bin/
        INCLUDES DESTINATION include/asio)

install(
        DIRECTORY "${PROJECT_SOURCE_DIR}/asio/include/"
        DESTINATION include
        FILES_MATCHING PATTERN "*.*hpp")

install(
        EXPORT asio-cmake
        FILE asio-config.cmake
        NAMESPACE asio::
        DESTINATION share/asio/cmake)