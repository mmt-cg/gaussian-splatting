cmake_minimum_required(VERSION 3.20)

project(DiffRast LANGUAGES CXX C)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_EXTENSIONS OFF)
# set(CMAKE_CUDA_STANDARD 17)
set(CMAKE_C_STANDARD 11)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

add_library(CpuRasterizer
    cpu_rasterizer/forward.c
    cpu_rasterizer/rasterizer_impl.c
    cpu_rasterizer/auxiliary.c
    # ...
)

set_target_properties(CpuRasterizer PROPERTIES LINKER_LANGUAGE C)

target_include_directories(CpuRasterizer PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/cpu_rasterizer)
