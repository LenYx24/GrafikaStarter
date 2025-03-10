cmake_minimum_required(VERSION 3.22)
project(GrafikaStarter)

# Jporta (jelenleg) c++17-el fordít, ajánlott ezt használni
set(CMAKE_CXX_STANDARD 17)

set(LIBDIR "${CMAKE_SOURCE_DIR}/Libraries")
set(GLFW_LIB "${LIBDIR}/glfw3/lib-vc2022/glfw3.lib")

set(CMAKE_CXX_FLAGS "-Wall -pedantic")

# A Libraries mappában is keresi a compiler a könyvtárakat, amiket beincludeolunk (emiatt nem kell relatív útvonalat írni)
include_directories(${LIBDIR})
find_package(OpenGL REQUIRED)

message("OPENGL LIBS: ${GLAD_LIBRARY}")

add_executable(GrafikaStarter
        # A "main.cpp"-t fogod feltölteni a jportára, nevezd át ha szeretnéd
        src/main.cpp

        src/framework.h
        src/framework.cpp
        Libraries/Glad/src/glad.c)


target_link_libraries(GrafikaStarter ${OPENGL_LIBRARIES} ${GLFW_LIB})