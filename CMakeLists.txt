cmake_minimum_required(VERSION 3.10)

set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "")

project(Nube)
add_executable(
    Nube
    src/Axis.cpp
    src/Camera.cpp
    src/Canvas.cpp
    src/Cloud.cpp
    src/Cumulus.cpp
    src/Exception.cpp
    src/FluidCPU.cpp
    src/Lsystem.cpp
    src/Main.cpp
    src/Metacloud.cpp
    src/Model.cpp
    src/Morph.cpp
    src/Mountain.cpp
    src/OBJLoader.cpp
    src/PrecomputeCPU.cpp
    src/Shader.cpp
    src/Tool.cpp    
)
target_include_directories(
    Nube
    PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/dependencies
    /opt/homebrew/include
)
set_property(TARGET Nube PROPERTY CXX_STANDARD 17)

find_package(glad CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package(OpenGL REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
target_include_directories(Nube PRIVATE ${OPENGL_INCLUDE_DIR})
target_link_libraries(Nube PRIVATE OpenGL::GL glfw glm::glm glad::glad)
target_compile_options(Nube PRIVATE)
