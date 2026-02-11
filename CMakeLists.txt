cmake_minimum_required(VERSION 3.10.0)

project(noa-json VERSION 0.1.0)

add_library(noa-json src/json.cpp)

target_compile_features(noa-json PUBLIC cxx_std_20)

target_include_directories(noa-json PUBLIC include)

if (PROJECT_IS_TOP_LEVEL)
    add_executable(test test.cpp)
    target_link_libraries(test noa-json)
endif()