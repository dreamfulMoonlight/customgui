set(PROJECT_SOURCES ${PROJECT_SOURCE_DIR}/src/main.cpp)

add_subdirectory(common)
add_subdirectory(imgui)
add_subdirectory(uiframe)

add_executable(customgui main.cpp)
