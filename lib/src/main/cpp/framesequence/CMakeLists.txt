cmake_minimum_required(VERSION 3.4.1)

project("framesequence")

SET(CMAKE_C_FLAGS "-Wall -Werror -Wno-unused-parameter -Wno-unused-variable -Wno-overloaded-virtual -fvisibility=hidden")

include_directories(utils)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(${CMAKE_SOURCE_DIR}/src/main/cpp/webp/include/webp)
include_directories(${CMAKE_SOURCE_DIR}/src/main/cpp/giflib)

set(SourceList

        BitmapDecoderJNI.cpp
        FrameSequence.cpp
        FrameSequenceJNI.cpp
        FrameSequence_webp.cpp
        JNIHelpers.cpp
        Registry.cpp
        Stream.cpp)

if(ENABLE_GIF)
    set(SourceList ${SourceList} FrameSequence_gif.cpp)
endif(ENABLE_GIF)

#生成动态库名称、类型、资源文件
add_library(framesequence

        SHARED

        ${SourceList})

#
find_library(log-lib log)
find_library(jnigraphics-lib jnigraphics)
LINK_DIRECTORIES(${CMAKE_LIBRARY_OUTPUT_DIRECTORY})
#

set(LibList

        framesequence
        ${log-lib}
        ${jnigraphics-lib}
        webp-decode)

if(ENABLE_GIF)
    set(LibList ${LibList} gif)
endif(ENABLE_GIF)

target_link_libraries(${LibList})