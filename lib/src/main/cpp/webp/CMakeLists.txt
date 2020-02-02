cmake_minimum_required(VERSION 3.4.1)

project("webp")

#继承上一层的CMakeLists.txt的变量，也可以在这里重新赋值
#C 的编译选项是 CMAKE_C_FLAGS
# 指定编译参数，可选
SET(CMAKE_C_FLAGS "-O2 -DANDROID -DWEBP_SWAP_16BIT_CSP -DWEBP_USE_THREAD -Wall -Werror")

# 配置头文件
#include_directories(${PROJECT_SOURCE_DIR}/include/webp)
#include_directories(${PROJECT_SOURCE_DIR}/src/dec)
#include_directories(${PROJECT_SOURCE_DIR}/src/demux)
#include_directories(${PROJECT_SOURCE_DIR}/src/dsp)
#include_directories(${PROJECT_SOURCE_DIR}/src/utils)
include_directories(include/webp)
include_directories(src/dec)
include_directories(src/demux)
include_directories(src/dsp)
include_directories(src/enc)
include_directories(src/mux)
include_directories(src/utils)
include_directories(src/webp)

#生成动态库名称、类型、资源文件
add_library(webp-decode

        SHARED

        src/dec/alpha_dec.c
        src/dec/buffer_dec.c
        src/dec/frame_dec.c
        src/dec/idec_dec.c
        src/dec/io_dec.c
        src/dec/quant_dec.c
        src/dec/tree_dec.c
        src/dec/vp8_dec.c
        src/dec/vp8l_dec.c
        src/dec/webp_dec.c
        src/demux/demux.c
        src/dsp/alpha_processing.c
        src/dsp/alpha_processing_mips_dsp_r2.c
        src/dsp/alpha_processing_sse2.c
        src/dsp/alpha_processing_sse41.c
        src/dsp/alpha_processing_neon.c
        src/dsp/cpu.c
        src/dsp/dec.c
        src/dsp/dec_clip_tables.c
        src/dsp/dec_mips32.c
        src/dsp/dec_mips_dsp_r2.c
        src/dsp/dec_msa.c
        src/dsp/dec_neon.c
        src/dsp/dec_sse2.c
        src/dsp/dec_sse41.c
        src/dsp/filters.c
        src/dsp/filters_mips_dsp_r2.c
        src/dsp/filters_msa.c
        src/dsp/filters_neon.c
        src/dsp/filters_sse2.c
        src/dsp/lossless.c
        src/dsp/lossless_mips_dsp_r2.c
        src/dsp/lossless_msa.c
        src/dsp/lossless_neon.c
        src/dsp/lossless_sse2.c
        src/dsp/rescaler.c
        src/dsp/rescaler_mips32.c
        src/dsp/rescaler_mips_dsp_r2.c
        src/dsp/rescaler_msa.c
        src/dsp/rescaler_neon.c
        src/dsp/rescaler_sse2.c
        src/dsp/upsampling.c
        src/dsp/upsampling_mips_dsp_r2.c
        src/dsp/upsampling_msa.c
        src/dsp/upsampling_neon.c
        src/dsp/upsampling_sse2.c
        src/dsp/upsampling_sse41.c
        src/dsp/yuv.c
        src/dsp/yuv_mips32.c
        src/dsp/yuv_mips_dsp_r2.c
        src/dsp/yuv_neon.c
        src/dsp/yuv_sse2.c
        src/dsp/yuv_sse41.c
        src/utils/bit_reader_utils.c
        src/utils/color_cache_utils.c
        src/utils/filters_utils.c
        src/utils/huffman_utils.c
        src/utils/quant_levels_dec_utils.c
        src/utils/random_utils.c
        src/utils/rescaler_utils.c
        src/utils/thread_utils.c
        src/utils/utils.c)

#依赖库
#find_library(log-lib log)
#
#target_link_libraries(one ${log-lib})