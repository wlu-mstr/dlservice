cmake_minimum_required(VERSION 3.7)
#project(TF_CPP_DETECT)

set(CMAKE_CXX_STANDARD 11)
ADD_COMPILE_OPTIONS(-fPIC)

include_directories(crow/include/)

set(SOURCE_FILES  main.cpp base64.cpp base64.h)
add_executable(test_crow ${SOURCE_FILES})
SET_TARGET_PROPERTIES(test_crow PROPERTIES PREFIX "")

# crow lib
#include_directories("/usr/local/include")

# OpenCV libs
find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})
target_link_libraries(test_crow ${OpenCV_LIBS})

# boost lib
find_package(Boost REQUIRED COMPONENTS system thread)
include_directories( ${Boost_INCLUDE_DIRS} )
target_link_libraries(test_crow ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY})

# pthread link
target_link_libraries(test_crow -lpthread -lm)