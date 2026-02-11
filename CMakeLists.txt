cmake_minimum_required(VERSION 3.10.0)

project(noa-json VERSION 0.2.0)

# This option is only useful for Noahh itself
if (DEFINED NOA_JSON_AS_INTERFACE AND NOA_JSON_AS_INTERFACE)
    add_library(noa-json INTERFACE)

    target_sources(noa-json INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/src/json.cpp)
    
    target_include_directories(noa-json INTERFACE include)
else()
    add_library(noa-json src/json.cpp)

    target_compile_features(noa-json PUBLIC cxx_std_20)
    
    target_include_directories(noa-json PUBLIC include)
endif()

if (PROJECT_IS_TOP_LEVEL)
    add_executable(test test.cpp)
    target_link_libraries(test noa-json)
endif()