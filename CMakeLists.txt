cmake_minimum_required(VERSION 3.5.0)
project(OE_ZMQ)
add_subdirectory(EventBroadcaster)
add_subdirectory(NetworkEvents)

#on windows, copy the dlls when installing
if (MSVC)
	if (NOT DEFINED GUI_BASE_DIR)
		if (DEFINED ENV{GUI_BASE_DIR})
			set(GUI_BASE_DIR $ENV{GUI_BASE_DIR})
		else()
			set(GUI_BASE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../plugin-GUI)
		endif()
	endif()

	set(GUI_BIN_DIR ${GUI_BASE_DIR}/Build/$<IF:$<CONFIG:Debug>,Debug,Release>)
	if (CMAKE_SIZEOF_VOID_P EQUAL 8)
		set(CMAKE_LIBRARY_ARCHITECTURE "x64")
	else()
		set(CMAKE_LIBRARY_ARCHITECTURE "x86")
	endif()
	install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/libs/bin/${CMAKE_LIBRARY_ARCHITECTURE}/ DESTINATION ${GUI_BIN_DIR}/shared CONFIGURATIONS ${CMAKE_CONFIGURATION_TYPES})

endif()