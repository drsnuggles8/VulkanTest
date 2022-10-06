project(VulkanTest
		LANGUAGES CXX)

# Externally provided content
add_subdirectory(vendor)

# Main targets built by this project
add_subdirectory(src)

# Vulkan stuff
message(STATUS "Using module to find Vulkan")
find_package(Vulkan)

target_include_directories("VulkanTest" PRIVATE
	src
	vendor/glfw-src/include
	vendor/glm-src
	${Vulkan_INCLUDE_DIRS}
)

target_compile_definitions("VulkanTest" PRIVATE
							_CRT_SECURE_NO_WARNINGS
							GLFW_INCLUDE_NONE
)

target_link_libraries(VulkanTest
					glfw
					${Vulkan_LIBRARIES}
					debug $ENV{VULKAN_SDK}/Lib/shaderc_sharedd.lib
					debug $ENV{VULKAN_SDK}/Lib/spirv-cross-cored.lib
					debug $ENV{VULKAN_SDK}/Lib/spirv-cross-glsld.lib
					debug $ENV{VULKAN_SDK}/Lib/SPIRV-Toolsd.lib
					optimized $ENV{VULKAN_SDK}/Lib/shaderc_shared.lib
					optimized $ENV{VULKAN_SDK}/Lib/spirv-cross-core.lib
					optimized $ENV{VULKAN_SDK}/Lib/spirv-cross-glsl.lib
)

if(MSVC)
	set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
	target_compile_options("VulkanTest" PRIVATE /W4)
endif()