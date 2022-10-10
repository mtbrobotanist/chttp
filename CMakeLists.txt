cmake_minimum_required(VERSION 3.5)


set(PROJECT_NAME chttp)
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

project(${PROJECT_NAME})
set(CMAKE_C_STANDARD 11)

# Assign the include directories
include_directories(include)

# Find library sources
set(LIB_SOURCE_FILES src/server.c)

# Build static/shared library
add_library(${PROJECT_NAME}_LIB STATIC ${LIB_SOURCE_FILES})

# Install library
install(TARGETS ${PROJECT_NAME}_LIB DESTINATION lib)

# Install library headers
set(LIB_INCLUDE_FILES include/http/http.h)
install(FILES ${LIB_INCLUDE_FILES} DESTINATION include)

add_executable(http_test test/main.c)
target_link_libraries(http_test ${PROJECT_NAME}_LIB)

# target_link_libraries(${PROJECT_NAME} ${PROJECT_NAME}_LIB)