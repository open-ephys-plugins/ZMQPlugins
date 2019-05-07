cmake_minimum_required(VERSION 3.5.0)
project(OE_ZMQ)
add_subdirectory(../EventBroadcaster/Builds EventBroadcaster)
add_subdirectory(../NetworkEvents/Builds NetworkEvents)

#on windows, copy the dlls when installing
if (MSVC)
	#change this if the base GUI code is located somewhere else
	set(GUI_BASE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../../plugin-GUI)

	set(GUI_BIN_DIR ${GUI_BASE_DIR}/Builds/VisualStudio2013)
	if (CMAKE_SIZEOF_VOID_P EQUAL 8)
		set(GUI_BIN_DIR ${GUI_BIN_DIR}/x64)
		set(CMAKE_LIBRARY_ARCHITECTURE "x64")
	else()
		set(CMAKE_LIBRARY_ARCHITECTURE "x86")
	endif()
	install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/../libs/bin/${CMAKE_LIBRARY_ARCHITECTURE}/ DESTINATION ${GUI_BIN_DIR}/Debug/bin/shared CONFIGURATIONS Debug)
	install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/../libs/bin/${CMAKE_LIBRARY_ARCHITECTURE}/ DESTINATION ${GUI_BIN_DIR}/Release/bin/shared CONFIGURATIONS Release)
endif()