set(SOURCES
		"main.cpp"
)

add_executable(VulkanTest
		${SOURCES}
)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR}
			FILES ${SOURCES}
)
