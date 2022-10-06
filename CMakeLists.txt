cmake_minimum_required(VERSION 3.24)

project(VulkanTutorial
        LANGUAGES CXX)

# Project wide setup
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS ON)
set_property(GLOBAL PROPERTY USE_FOLDERS YES)
set_property(GLOBAL PROPERTY PREDEFINED_TARGETS_FOLDER "cmake")

# Main targets built by this project
add_subdirectory(VulkanTest)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT "VulkanTest")
