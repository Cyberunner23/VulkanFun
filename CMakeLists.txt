cmake_minimum_required(VERSION 3.7)


#------------------------------------------------------------------------------
# CMake Policies
#------------------------------------------------------------------------------

if(POLICY CMP0054)
    cmake_policy(SET CMP0054 NEW)
endif()


#------------------------------------------------------------------------------
# Hunter & Project
#------------------------------------------------------------------------------

include("cmake/HunterGate.cmake")

HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.20.62.tar.gz"
    SHA1 "10ffae63cf7b07193d6d7b459c1d0cfa242fad5b"
)

project(VulkanFun)


#------------------------------------------------------------------------------
# Config
#------------------------------------------------------------------------------

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED true)


#------------------------------------------------------------------------------
# Deps
#------------------------------------------------------------------------------

hunter_add_package(glfw)
find_package(glfw3 CONFIG REQUIRED)

hunter_add_package(glm)
find_package(glm CONFIG REQUIRED)

find_package(Vulkan REQUIRED)


#------------------------------------------------------------------------------
# Source files
#------------------------------------------------------------------------------

set(SRC
    src/main.cpp
)


#------------------------------------------------------------------------------
# Executable
#------------------------------------------------------------------------------
add_executable(VulkanFun ${SRC})
target_link_libraries(VulkanFun 
    glfw
    glm
    Vulkan::Vulkan
)


