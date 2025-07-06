cmake_minimum_required(VERSION 3.10)
project(SFMLCMakeProject)

set(CMAKE_CXX_STANDARD 17)

# SFML 路径
set(SFML_INCLUDE_DIR "E:/Libraries/SFML-3.0.0/include")
set(SFML_LIB_DIR "E:/Libraries/SFML-3.0.0/lib")

# 添加头文件路径
include_directories(${SFML_INCLUDE_DIR})

# 添加可执行文件
add_executable(app src/main.cpp)

# 定义 SFML_STATIC 宏（关键）
target_compile_definitions(app PRIVATE SFML_STATIC)

# 链接 SFML 静态库
target_link_libraries(app PRIVATE
    ${SFML_LIB_DIR}/libsfml-graphics-s.a
    ${SFML_LIB_DIR}/libsfml-window-s.a
    ${SFML_LIB_DIR}/libsfml-system-s.a
    ${SFML_LIB_DIR}/libfreetype.a
    -lopengl32
    -lwinmm
    -lgdi32
)