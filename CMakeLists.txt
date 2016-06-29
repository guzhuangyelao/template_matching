cmake_minimum_required(VERSION 2.8)
project(template_matching)

set(CMAKE_CXX_COMPILER "/opt/intel/bin/icpc")
set(OPTIMIZATION "-ipo -O3 -fargument-noalias -align -ansi-alias -axCORE-AVX2 -restrict -fno-exceptions -fp-model fast=2 -no-prec-div")
set(VEC_REPORT 1)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -ansi -openmp -std=c++11 -static-intel ${OPTIMIZATION} -vec-report=${VEC_REPORT}")

include_directories(includes)
link_directories(
    /opt/intel/lib/intel64
)
set(SOURCE_FILE src/main.cpp src/sampling.cpp src/colorimage.cpp)
add_executable(template_match ${SOURCE_FILE})
target_link_libraries(template_match
    )