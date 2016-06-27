project(lua53)
cmake_minimum_required(VERSION 2.8)

# default to Debug build
if (NOT CMAKE_BUILD_TYPE)
    set( CMAKE_BUILD_TYPE Debug CACHE STRING "Sets the configuration to build (Release, Debug, etc...)")
endif()

set(LIB_NAME lua53)

include_directories(src)

set (SRC_LIB src/lapi.c src/lcode.c src/lctype.c src/ldebug.c
    src/ldo.c src/ldump.c src/lfunc.c src/lgc.c src/llex.c
    src/lmem.c src/lobject.c src/lopcodes.c src/lparser.c
    src/lstate.c src/lstring.c src/ltable.c src/ltm.c
    src/lundump.c src/lvm.c src/lzio.c src/lauxlib.c
    src/lbaselib.c src/lbitlib.c src/lcorolib.c src/ldblib.c
    src/liolib.c src/lmathlib.c src/loslib.c src/lstrlib.c
    src/ltablib.c src/lutf8lib.c src/loadlib.c src/linit.c)

add_library(${LIB_NAME} SHARED ${SRC_LIB})

add_library(${LIB_NAME}_static ${SRC_LIB})
set_target_properties(${LIB_NAME}_static PROPERTIES OUTPUT_NAME ${LIB_NAME})
