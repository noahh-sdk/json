cmake_minimum_required(VERSION 3.21)

project(noa-json VERSION 2.0.0)

# This option is only useful for Noahh itself
if (DEFINED NOA_JSON_AS_INTERFACE AND NOA_JSON_AS_INTERFACE)
    add_library(noa-json INTERFACE)
    target_include_directories(noa-json INTERFACE include)

    add_library(noa-json-impl INTERFACE)

    target_link_libraries(noa-json-impl noa-json)
    target_sources(noa-json-impl INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/src/json.cpp)
else()
    add_library(noa-json src/json.cpp)

    target_compile_features(noa-json PUBLIC cxx_std_20)
    
    target_include_directories(noa-json PUBLIC include)
endif()

if (PROJECT_IS_TOP_LEVEL)
    add_subdirectory(test)
endif()