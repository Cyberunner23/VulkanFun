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
    URL "https://github.com/ruslo/hunter/archive/v0.20.63.tar.gz"
    SHA1 "358385a57457e5276f9e9db6e8e2bc80c53287ad"
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


