cmake_minimum_required(VERSION 3.20)
project(StrelkaMetal LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)

set(RUNNER_SOURCES
    ./source/main_gui.mm
    ./source/help.cpp
    ./externals/imgui/src/imgui.cpp
    ./externals/imgui/src/imgui_draw.cpp
    ./externals/imgui/src/imgui_impl_glfw.cpp
    ./externals/imgui/src/imgui_tables.cpp
    ./externals/imgui/src/imgui_widgets.cpp
    ./externals/imgui/src/imgui_impl_metal.mm
    ./externals/imgui/src/imgui_demo.cpp)
set(RUNNER_NAME Runner)

add_executable(${RUNNER_NAME} ${RUNNER_SOURCES})

target_include_directories(${RUNNER_NAME} PUBLIC ./shaders/)
target_include_directories(${RUNNER_NAME}
                           PUBLIC ./externals/glfw-3.3.8.bin.MACOS/include)
target_include_directories(${RUNNER_NAME} PUBLIC ./externals/imgui/include)
target_include_directories(${RUNNER_NAME} PUBLIC ./externals/imgui/src)
target_include_directories(${RUNNER_NAME} PUBLIC ./externals/metal-cpp/)
target_include_directories(${RUNNER_NAME}
                           PUBLIC ./externals/metal-cpp-extensions/)

target_link_libraries(${RUNNER_NAME} "-framework Foundation")
target_link_libraries(${RUNNER_NAME} "-framework QuartzCore")
target_link_libraries(${RUNNER_NAME} "-framework Metal")
target_link_libraries(${RUNNER_NAME} "-framework MetalKit")
target_link_libraries(
  ${RUNNER_NAME}
  "${CMAKE_SOURCE_DIR}/externals/glfw-3.3.8.bin.MACOS/lib-arm64/libglfw.3.dylib"
)
