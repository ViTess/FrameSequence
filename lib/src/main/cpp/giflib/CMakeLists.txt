cmake_minimum_required(VERSION 3.4.1)

SET(CMAKE_C_FLAGS "-Werror -Wno-format -Wno-sign-compare -Wno-unused-parameter -DHAVE_CONFIG_H")

add_library(gif

            SHARED

            dgif_lib.c
            egif_lib.c
            gifalloc.c
            gif_err.c
            gif_hash.c
            openbsd-reallocarray.c
            quantize.c)
