#CMake版本最低要求3.12
cmake_minimum_required(VERSION 3.12)

#工程名称
project(Vulkan-Learning-Project)

#遵循C++20标准
set(CMAKE_CXX_STANDARD 20)

add_definitions(-DDEBUG)

#GLFW头文件目录
include_directories(
	SYSTEM ${CMAKE_CURRENT_SOURCE_DIR}/ThirdParty/GLFW/include
)

#GLFW链接目录
link_directories(
	SYSTEM ${CMAKE_CURRENT_SOURCE_DIR}/ThirdParty/GLFW/lib-mingw-w64
)

#Vulkan
find_package(Vulkan REQUIRED)
include_directories(${Vulkan_INCLUDE_DIRS})

#源文件列表
set(SRC_LIST Programs/Main.cpp)

#可执行文件
add_executable(VulkanApp ${SRC_LIST})

#需要链接的库文件
target_link_libraries(VulkanApp ${Vulkan_LIBRARIES} glfw3)


