project(Zombicus-cpp)

cmake_minimum_required(VERSION 3.13)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -Wall -Wextra")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Werror=missing-field-initializers -Werror=return-type")

set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${GCC_COVERAGE_LINK_FLAGS} -I/usr/local/lib -I/opt/homebrew/lib -framework OpenGL -framework Cocoa -framework IOKit -framework CoreVideo")

# find_package(glfw3 3.3 REQUIRED)
# find_package(OpenGL REQUIRED)

add_subdirectory(imgui imgui)
add_subdirectory(glfw glfw)

include_directories(
  SYSTEM
  ${CMAKE_SOURCE_DIR}/glfw
  ${CMAKE_SOURCE_DIR}/imgui
  ${CMAKE_SOURCE_DIR}/imgui/backends
)

add_executable(Zombicus-cpp src/Main.cpp)

target_link_libraries(Zombicus-cpp imgui glfw)
