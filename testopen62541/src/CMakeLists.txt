cmake_minimum_required(VERSION 3.5)
project(testopen62541)

set (${PROJECT_NAME}_VERSION_MAJOR 0)
set (${PROJECT_NAME}_VERSION_MINOR 0)
set (${PROJECT_NAME}_VERSION_PATCH 1)
set (${PROJECT_NAME}_VERSION
    "${${PROJECT_NAME}_VERSION_MAJOR}.${${PROJECT_NAME}_VERSION_MINOR}.${${PROJECT_NAME}_VERSION_PATCH}")

add_definitions(-DPROG=\"${PROJECT_NAME}\")
add_definitions(-std=c99)

FILE(GLOB SRC_FILES "src/*.c")

find_package(PkgConfig REQUIRED)

pkg_check_modules(OPEN62541 REQUIRED IMPORTED_TARGET open62541)

add_executable(${PROJECT_NAME} ${SRC_FILES})
target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_BINARY_DIR}
    )
target_link_libraries(${PROJECT_NAME} PRIVATE
    ${OPEN62541_LIBRARIES}
    )

INSTALL(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION /usr/bin/)