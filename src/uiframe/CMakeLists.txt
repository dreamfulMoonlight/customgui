file(GLOB_RECURSE _HEADERS
    *.h
    mainuiset/*.h
    configuiset/*.h
   )

file(GLOB_RECURSE _SOURCES
    *.cpp
    mainuiset/*.cpp
    configuiset/*.cpp
   )


set(HEADERS ${_HEADERS})
set(SOURCES ${_SOURCES})

set(UIFRAME_SOURCES ${HEADERS} ${SOURCES})

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${UIFRAME_SOURCES})
