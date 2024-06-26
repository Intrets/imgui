cmake_minimum_required(VERSION 3.18)

set(MODULE_NAME imgui)

project(${MODULE_NAME} LANGUAGES CXX)

add_library(${MODULE_NAME}
	imgui.h imgui.cpp
	imgui_demo.cpp
	imgui_draw.cpp
	imgui_internal.h
	imgui_tables.cpp
	imgui_widgets.cpp
	imstb_rectpack.h
	imstb_textedit.h
	imstb_truetype.h
	backends/imgui_impl_opengl3.h backends/imgui_impl_opengl3.cpp
	backends/imgui_impl_opengl3_loader.h
	misc/cpp/imgui_stdlib.h misc/cpp/imgui_stdlib.cpp
)

target_compile_definitions(${MODULE_NAME} PUBLIC ImTextureID=GLuint)

target_link_libraries(${MODULE_NAME}
	PUBLIC
		wrangled_gl
)

target_include_directories(
	${MODULE_NAME} PUBLIC
		.
		backends
		misc/cpp
)


add_library(${MODULE_NAME}_glfw
	backends/imgui_impl_glfw.h backends/imgui_impl_glfw.cpp
)

#find_package(GLFW3 REQUIRED)
#target_link_libraries(${MODULE_NAME}_glfw
#	PUBLIC
#        GLFW3
#		imgui
#)

target_include_directories(
	${MODULE_NAME}_glfw PUBLIC
		backends
)
