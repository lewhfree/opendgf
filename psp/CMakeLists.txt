cmake_minimum_required(VERSION 3.5)

project(opendgf)
set(SOURCES src/opendgf.c)
add_executable(${PROJECT_NAME} ${SOURCES})

include(FindPkgConfig)
pkg_search_module(SDL2 REQUIRED sdl2)

target_include_directories(${PROJECT_NAME} PRIVATE ${SDL2_INCLUDE_DIRS} PRIVATE include/)

target_link_libraries(${PROJECT_NAME} PRIVATE
    ${SDL2_LIBRARIES}
)

if(PSP)
    create_pbp_file(
        TARGET ${PROJECT_NAME}
        ICON_PATH NULL
        BACKGROUND_PATH NULL
        PREVIEW_PATH NULL
        TITLE ${PROJECT_NAME}
        VERSION 00.01
    )
endif()
