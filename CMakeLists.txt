cmake_minimum_required(VERSION 3.16)
project(EdgesCGALDelaunay2D LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(CGAL REQUIRED)

add_executable(EdgesCGALDelaunay2D src/EdgesCGALDelaunay2D.cpp)
target_link_libraries(EdgesCGALDelaunay2D PRIVATE CGAL::CGAL)
target_compile_options(EdgesCGALDelaunay2D PRIVATE -O3 -DNDEBUG)