cmake_minimum_required(VERSION 3.4.1)

#设为TRUE则编译GIF
set(ENABLE_GIF FALSE)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/jniLibs/${ANDROID_ABI})

message("------${ENABLE_GIF}------")

if(ENABLE_GIF)
    ADD_SUBDIRECTORY(${PROJECT_SOURCE_DIR}/src/main/cpp/giflib)
endif(ENABLE_GIF)
ADD_SUBDIRECTORY(${PROJECT_SOURCE_DIR}/src/main/cpp/webp)
ADD_SUBDIRECTORY(${PROJECT_SOURCE_DIR}/src/main/cpp/framesequence)