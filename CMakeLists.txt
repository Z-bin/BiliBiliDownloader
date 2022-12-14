cmake_minimum_required(VERSION 3.15)

project(B23Downloader VERSION 0.95 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets Network)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets Network)

set(PROJECT_SOURCES
    MainWindow.cpp
    QrCode.cpp
    main.cpp
    )

if(${QT_VERSION_MAJOR} GREATER_EQUAL 6)
    qt_add_executable(B23Downloader
        MANUAL_FINALIZATION
        ${PROJECT_SOURCES}
        )
else()
    add_executable(B23Downloader
            ${PROJECT_SOURCES}
            )
endif()

target_link_libraries(B23Downloader PRIVATE Qt${QT_VERSION_MAJOR}::Widgets Qt${QT_VERSION_MAJOR}::Network)
