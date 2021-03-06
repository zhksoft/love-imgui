CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

project(imgui)

#SET(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
#FIND_PACKAGE(LuaJIT REQUIRED)

SET(LIB_NAME imgui)

ADD_LIBRARY(${LIB_NAME}
	MODULE
	src/libimgui/imconfig.h
	src/libimgui/imgui.cpp
	src/libimgui/imgui.h
	src/libimgui/imgui_draw.cpp
	src/libimgui/imgui_demo.cpp
	src/libimgui/imgui_internal.h
	src/libimgui/imgui_dock.cpp
	src/libimgui/imgui_dock.h
	src/libimgui/stb_rect_pack.h
	src/libimgui/stb_textedit.h
	src/libimgui/stb_truetype.h
	src/imgui_impl.cpp
	src/wrap_imgui_impl.cpp
	src/imgui_impl.h
	src/wrap_imgui_impl.h
	src/imgui_iterator.h
	src/imgui_iterator_dock.h
)

TARGET_INCLUDE_DIRECTORIES(${LIB_NAME}
	PUBLIC
	${LUAJIT_INCLUDE_DIR}
)

TARGET_LINK_LIBRARIES(${LIB_NAME}
	${LUAJIT_LIBRARY}
)

SET_TARGET_PROPERTIES(${LIB_NAME} PROPERTIES PREFIX "")

IF(DEFINED "LIB_DIR")
	INSTALL(TARGETS ${LIB_NAME} LIBRARY DESTINATION ${LIB_DIR})
ENDIF()
