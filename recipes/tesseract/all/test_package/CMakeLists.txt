cmake_minimum_required(VERSION 3.1)
project(test_package)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(Tesseract REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.cpp)
if(TARGET Tesseract::libtesseract)
    target_link_libraries(${PROJECT_NAME} Tesseract::libtesseract)
else()
    target_link_libraries(${PROJECT_NAME} libtesseract)
endif()
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 11)
