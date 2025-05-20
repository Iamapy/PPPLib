PROJECT(PPPLib)
#CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
CMAKE_MINIMUM_REQUIRED(VERSION 3.10)
CMAKE_POLICY(SET CMP0015 NEW)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_FLAGS "-std=c++11 -fPIC")
set(CMAKE_CXX_COMPILE "g++")
set(CMAKE_C_COMPILE "gcc")
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

#find_package(PythonLibs)
find_package(Python REQUIRED COMPONENTS Interpreter Development)
# 设置兼容性变量，用于旧的代码
set(PYTHON_INCLUDE_DIRS ${Python_INCLUDE_DIRS})
set(PYTHON_LIBRARIES ${Python_LIBRARIES})

# 输出Python库信息用于调试
message(STATUS "Python Include Dirs: ${PYTHON_INCLUDE_DIRS}")
message(STATUS "Python Libraries: ${PYTHON_LIBRARIES}")


include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/3rdparty)
include_directories(${PROJECT_SOURCE_DIR}/3rdparty/Eigen)
IF(WIN32)
    include_directories(${PROJECT_SOURCE_DIR}/windows)
ENDIF()

add_subdirectory(src)
add_subdirectory(exe)