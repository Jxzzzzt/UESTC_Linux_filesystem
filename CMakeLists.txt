cmake_minimum_required(VERSION 3.9)

project(filesystem)

# 查找 OpenSSL 库
find_package(OpenSSL REQUIRED)

# Add GTK2
find_package(PkgConfig REQUIRED)
pkg_check_modules (GTK2 REQUIRED gtk+-2.0)
set(CMAKE_C_STANDARD 11)
include_directories (${GTK2_INCLUDE_DIRS})
link_directories (${GTK2_LIBRARY_DIRS})
add_definitions (${GTK2_CFLAGS_OTHER})

# Add lib
add_subdirectory(./lib)


#Add filesysytem
aux_source_directory(./filesystem fs)
add_executable(filesystem ${fs})
