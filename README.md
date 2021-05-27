# lab03

Zadanie 1

sudo apt install cmake

cd formatter_lib

cat >> CMakeLists.txt << EOF
> cmake_minimum_required(VERSION 2.8)
> add_library(formatter STATIC formatter.h formatter.cpp)
> EOF

cmake CMakeLists.txt

cd .. 


Zadanie 2


cp -r  formatter_ex_lib formatter_lib


cd formatter_lib

cat >> CMakeLists.txt  << EOF
> cmake_minimum_required(VERSION 2.8)
> project(my_formatter_ex)
> include_directories(formatter_lib)
> add_subdirectory(formatter_lib)
> add_library(formatter_ex STATIC formatter_ex.h formatter_ex.cpp)
> target_link_libraries(formatter_ex formatter)
> EOF

Zadanie 3.1

cp -r formatter_ex hello_world_aplication

cat >> CMakesLists.txt <<EOF
>cmake_minimum_required(VERSION 2.8)
>project(hello_world)
>include_directories(formatter_ex_lib)
>add_subdirectory(formatter_ex_lib)
>add_executable(hello_world hello_world.cpp)
>target_link_libraries(hello_world formatter_ex)
EOF

make

./hello_world

Zadanie 3.2

redacted  ..... .cpp 
include<math.h>

sqrtf заменил на sqrt

CMakeLists.txt для _lib

cmake_minimum_required(VERSION 2.8)
add_library(solver_lib STATIC solver.h solver.cpp)

CMakeLists.txt для _aplication

cmake_minimum_required(VERSION 2.8)
project(solver)
add_executable(solver equation.cpp)
include_directories(formatter_ex_lib)
add_subdirectory(formatter_ex_lib)
include_directories(solver_lib)
add_subdirectory(solver_lib)
target_link_libraries(solver formatter_ex)
target_link_libraries(solver solver_lib)
