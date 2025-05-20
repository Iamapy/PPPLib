PROJECT(OutLib)
#CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
CMAKE_MINIMUM_REQUIRED(VERSION 3.10)
CMAKE_POLICY(SET CMP0015 NEW)

file(GLOB SRC_FILES "*.cc")
add_library(OutLib ${SRC_FILES})
#target_include_directories(OutLib PRIVATE ${PYTHON_INCLUDE_DIRS})
#target_link_libraries(OutLib CmnLib ${PYTHON_LIBRARIES})

# 如果使用新版Python查找模块
if(DEFINED Python_INCLUDE_DIRS)
    target_include_directories(OutLib PRIVATE ${Python_INCLUDE_DIRS})
    target_link_libraries(OutLib CmnLib ${Python_LIBRARIES})
else()
    # 兼容旧版查找模块
    target_include_directories(OutLib PRIVATE ${PYTHON_INCLUDE_DIRS})
    target_link_libraries(OutLib CmnLib ${PYTHON_LIBRARIES})
endif()