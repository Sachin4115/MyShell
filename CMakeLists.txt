# Specify the minimum version of CMake required
cmake_minimum_required(VERSION 4.0.1)

# Define the project name, version, and language (C++)
project(myshell VERSION 0.1 LANGUAGES CXX)

# Specify the C++ standard to use (C++17 is a good choice)
set(CMAKE_CXX_STANDARD 17)
# Enforce the standard, don't allow compiler to downgrade
set(CMAKE_CXX_STANDARD_REQUIRED True)
# Optional: Enable extensions if needed, but usually better to stick to standard
# set(CMAKE_CXX_EXTENSIONS OFF)

# Add the executable target
# This tells CMake to create an executable named 'main'
# from the source file 'main.cpp'
add_executable(main src/main.cpp)

# Optional: Add compiler warnings (good practice)
# This depends on your compiler (GCC/MinGW in this case)
# 'if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")' checks if the compiler is GCC (like MinGW).
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
# 'target_compile_options()' applies options to a specific target ('main').
# 'PRIVATE' means these options are only for building 'main' itself, not for
# anything that might link against it (less relevant for executables).
# -Wall: Enable most standard warnings.
# -Wextra: Enable some extra warnings not covered by -Wall.
# -pedantic: Issue warnings required by the strict C++ standard.
target_compile_options(main PRIVATE -Wall -Wextra -pedantic)
endif()