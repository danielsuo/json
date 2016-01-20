cmake_minimum_required(VERSION 2.8)

project(json CXX)

# add_executable(json_unit
#     src/json.hpp test/catch.hpp test/unit.cpp
# )

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)
# add_library(json src/json.hpp)
SET_TARGET_PROPERTIES(json PROPERTIES LINKER_LANGUAGE CXX)

if(MSVC)
    set(CMAKE_CXX_FLAGS
        "/EHsc"
    )

    STRING(REPLACE "/O2" "/Od" CMAKE_CXX_FLAGS_RELEASE ${CMAKE_CXX_FLAGS_RELEASE})

    add_definitions(-D_SCL_SECURE_NO_WARNINGS)
else(MSVC)
    set(CMAKE_CXX_FLAGS
        "-std=c++11"
    )
endif(MSVC)

include_directories(
    src test
)
