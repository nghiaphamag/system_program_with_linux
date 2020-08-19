cmake_minimum_required (VERSION 3.7)
project(ex1_cmakeproject)

include_directories(${CMAKE_SOURCE_DIR}/include)
link_directories(${CMAKE_SOURCE_DIR}/lib)

set(SOURCES src/prog1.c)
add_executable(myexe ${PROJECT_SOURCE_DIR}/${SOURCES})

target_link_libraries(myexe libc.so libarifmath.a)

install(TARGETS myexe DESTINATION /usr/bin)
install(FILES man/myadd.3 DESTINATION /usr/share/man/man3)


include(InstallRequiredSystemLibraries)
set(CPACK_GENERATOR "DEB")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "NekoBot")
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED True)
include(CPack)

