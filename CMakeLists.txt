cmake_minimum_required(VERSION 3.14)

set(TARGET_APP "Qt-QrCodeGenerator")
project(${TARGET_APP} LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Gui Svg)

add_library(${TARGET_APP} STATIC
    src/QrCodeGenerator.h src/QrCodeGenerator.cpp
    src/qrcodegen/qrcodegen.h src/qrcodegen/qrcodegen.cpp
)

target_link_libraries(${TARGET_APP} PRIVATE Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Gui Qt${QT_VERSION_MAJOR}::Svg)

target_compile_definitions(${TARGET_APP} PRIVATE QRCODEGENERATOR_LIBRARY)
