# ---- Set cmake minimum version ---------------
cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
cmake_policy(SET CMP0048 NEW)

# ---- Set project details ---------------------
project(celeste_rn VERSION 0.0.1 LANGUAGES CXX)

# ---- Configure compiler ----------------------
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++ -std=c++11")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g -Wall -Wextra")

set(CMAKE_CXX_STANDARD 11)
set(CXX_STANDARD TRUE)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)


# ---- Source ---------------------------------
include_directories("src/")
file(GLOB_RECURSE CELESTERN_SRC
    "src/*.cpp"
    )
set(celeste_rn ${CELESTERN_SRC})

file(GLOB_RECURSE CELESTERN_HEADERS
    "src/*.hpp"
    )


# ---- Add our own CelesteRN library -----------
add_library(celeste_rn SHARED ${celeste_rn})
set_target_properties(celeste_rn PROPERTIES LINKER_LANGUAGE CXX)