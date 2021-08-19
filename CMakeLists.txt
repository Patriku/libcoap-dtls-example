cmake_minimum_required(VERSION 3.20)
project(example C)

set(CMAKE_C_STANDARD 11)

find_package(PkgConfig REQUIRED)
pkg_check_modules(libcoap-3 REQUIRED IMPORTED_TARGET libcoap-3)

add_executable(server server.c shared.c shared.h)
add_executable(client client.c shared.c shared.h)

target_link_libraries(server PUBLIC PkgConfig::libcoap-3)
target_link_libraries(client PUBLIC PkgConfig::libcoap-3)