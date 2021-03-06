if (USE_VULKAN)
	set(IMGUI_IMPL_VULKAN_SOURCES
		include/gui/imgui_impl_sdl_vulkan.h

		src/imgui_impl_sdl_vulkan.cpp
	)
else()
	set(IMGUI_IMPL_VULKAN_SOURCES "")
endif()

add_library(
	gui
	STATIC
	include/gui/functions.h
	include/gui/imgui_impl_sdl_gl3.h
	include/gui/imgui_impl_sdl_state.h
	include/gui/imgui_impl_sdl.h
	include/gui/state.h
	src/common_dialog.cpp
	src/condvars_dialog.cpp
	src/eventflags_dialog.cpp
	src/game_selector.cpp
	src/gui.cpp
	src/imgui_impl_sdl_gl3.cpp
	${IMGUI_IMPL_VULKAN_SOURCES}
	src/imgui_impl_sdl.cpp
	src/main_menubar.cpp
	src/mutexes_dialog.cpp
	src/perf_overlay.cpp
	src/private.h
	src/reinstall.cpp
	src/semaphores_dialog.cpp
	src/settings_dialog.cpp
	src/threads_dialog.cpp
	src/controls_dialog.cpp
	src/allocations_dialog.cpp
	src/disassembly_dialog.cpp
	src/about_dialog.cpp
	src/trophy_unlocked.cpp
)

target_include_directories(gui PUBLIC include)
target_link_libraries(gui PUBLIC host imgui glutil)
target_link_libraries(gui PRIVATE stb renderer)
