cmake_minimum_required(VERSION 3.10) # 设置最低版本

project(DuoLink VERSION 1.0.0 LANGUAGES C CXX) # 设置项目名称和版本

# add_definitions(-D宏名称) # 添加宏定义
add_definitions(-DDEBUG) # 自定义 DEBUG 宏

# PROJECT 指令的语法是：
# project(<PROJECT-NAME> [<language-name>...])project(<PROJECT-NAME>
#        [VERSION <major>[.<minor>[.<patch>[.<tweak>]]]]
#        [DESCRIPTION <project-description-string>]
#        [HOMEPAGE_URL <url-string>]
#        [LANGUAGES <language-name>...])

# 设置编译器标准
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17) # 设置 C++ 标准为 C++11
# set(CMAKE_CXX_STANDARD 14) # 设置 C++ 标准为 C++14
# set(CMAKE_CXX_STANDARD 17) # 设置 C++ 标准为 C++17
# set(CMAKE_CXX_STANDARD_REQUIRED ON) #强制使用以上标准

# set(SRC_LIST src/main.c src/add.c src/sub.c src/mult.c src/div.c) # 手动设置源文件
# aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST) # 自动查找源文件

message(STATUS "source path: ${PROJECT_SOURCE_DIR}") # 输出一般日志信息
# message(WARNING "source path: ${PROJECT_SOURCE_DIR}") # 输出警告信息
# message(FATAL_ERROR "source path: ${PROJECT_SOURCE_DIR}") # 输出错误信息

include_directories(${PROJECT_SOURCE_DIR}/inc) # 添加头文件路径
file(GLOB SRC_LIST "${CMAKE_CURRENT_SOURCE_DIR}/src/*.c") # 查找当前目录下的所有源文件

# link_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib) # 链接库文件路径
# link_libraries(libcmakel.a) # 链接静态库

# add_library(cmakel STATIC ${SRC_LIST}) # 添加静态库
# add_library(cmakel SHARED ${SRC_LIST}) # 添加动态库

# 移除 main.cpp
# file(GLOB SRC_1 ${PROJECT_SOURCE_DIR}/*.c)
# list(REMOVE_ITEM SRC_1 ${PROJECT_SOURCE_DIR}/main.c)

# 追加(拼接)
# set(TEMP "hello,world")
# file(GLOB SRC_1 ${PROJECT_SOURCE_DIR}/src1/*.c)
# file(GLOB SRC_2 ${PROJECT_SOURCE_DIR}/src2/*.c)
# list(APPEND SRC_3 ${SRC_1} ${SRC_2} ${TEMP})

# 拼接
# set(SRC_4 ${SRC_1} ${SRC_2} ${TEMP})
add_executable(DuoLink ${SRC_LIST}) # 添加可执行文件
# target_link_libraries(CMAKEL libcmakel.dll) # 链接动态库 要在 add_executable 之后

# 设置输出目录.
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin) # 设置可执行文件输出目录
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib) # 设置库文件输出目录
