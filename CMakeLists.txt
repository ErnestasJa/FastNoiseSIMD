cmake_minimum_required (VERSION 2.6)
project (FastNoise)
set(CPP_GCC_COMPILE_FLAGS "${CMAKE_CXX_FLAGS} -msse4.1")

include_directories(
        "FastNoiseSIMD"
)

set(BUILD_SOURCES
        "FastNoiseSIMD/FastNoiseSIMD.cpp"
        #"FastNoiseSIMD/FastNoiseSIMD_avx2.cpp"
        #"FastNoiseSIMD/FastNoiseSIMD_avx512.cpp"
        #"FastNoiseSIMD/FastNoiseSIMD_internal.cpp"
        #"FastNoiseSIMD/FastNoiseSIMD_neon.cpp"
        #"FastNoiseSIMD/FastNoiseSIMD_sse2.cpp"
        "FastNoiseSIMD/FastNoiseSIMD_sse41.cpp"
        #"FastNoiseSIMD/ARM/cpu-features.c"
        )

add_library(FastNoise STATIC ${BUILD_SOURCES})
set_target_properties(FastNoise PROPERTIES COMPILE_FLAGS "${CPP_GCC_COMPILE_FLAGS}")

