cmake_minimum_required(VERSION 3.4.1)

#继承上一层的CMakeLists.txt的变量，也可以在这里重新赋值
#C 的编译选项是 CMAKE_C_FLAGS
# 指定编译参数，可选
SET(CMAKE_C_FLAGS "-Werror -Wno-format -Wno-sign-compare -Wno-unused-parameter -DHAVE_CONFIG_H")

#生成动态库名称、类型、资源文件
add_library(gif

            SHARED

            dgif_lib.c
            egif_lib.c
            gifalloc.c
            gif_err.c
            gif_hash.c
            openbsd-reallocarray.c
            quantize.c)

#依赖库
#find_library(log-lib log)
#
#target_link_libraries(one ${log-lib})