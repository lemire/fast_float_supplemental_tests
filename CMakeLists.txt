cmake_minimum_required(VERSION 3.15)

project(SupplementalFastFloatBenchmark VERSION 0.1.0 LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)

FetchContent_Declare(
  fast_float
  GIT_REPOSITORY https://github.com/lemire/fast_float.git
  GIT_TAG origin/main
  GIT_SHALLOW TRUE)

FetchContent_MakeAvailable(fast_float)
add_subdirectory(data)



target_compile_options(fast_float INTERFACE -fsanitize=address -fno-omit-frame-pointer -fsanitize=undefined -fno-sanitize-recover=all)
target_link_libraries(fast_float INTERFACE -fsanitize=address -fno-omit-frame-pointer -fsanitize=undefined -fno-sanitize-recover=all)
if (CMAKE_COMPILER_IS_GNUCC)
    target_link_libraries(fast_float INTERFACE -fuse-ld=gold)
endif()

enable_testing()
add_subdirectory(tests)