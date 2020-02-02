cmake_minimum_required(VERSION 3.4.1)

project("framesequence")

#继承上一层的CMakeLists.txt的变量，也可以在这里重新赋值
#C 的编译选项是 CMAKE_C_FLAGS
# 指定编译参数，可选
SET(CMAKE_C_FLAGS "-Wall -Werror -Wno-unused-parameter -Wno-unused-variable -Wno-overloaded-virtual -fvisibility=hidden")

include_directories(utils)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(${CMAKE_SOURCE_DIR}/src/main/cpp/webp/include/webp)
include_directories(${CMAKE_SOURCE_DIR}/src/main/cpp/giflib)

#生成动态库名称、类型、资源文件
add_library(framesequence

        SHARED

        BitmapDecoderJNI.cpp
        FrameSequence.cpp
        FrameSequenceJNI.cpp
#        FrameSequence_gif.cpp
        FrameSequence_webp.cpp
        JNIHelpers.cpp
        Registry.cpp
        Stream.cpp)

#依赖库
find_library(log-lib log)
find_library(jnigraphics-lib jnigraphics)
LINK_DIRECTORIES(${CMAKE_LIBRARY_OUTPUT_DIRECTORY})
#
target_link_libraries(framesequence ${log-lib} ${jnigraphics-lib} webp-decode)