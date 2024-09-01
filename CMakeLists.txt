cmake_minimum_required(VERSION 3.10)

project(WatchySim VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)

# Define source files
set(SOURCES
        WatchySim/arduino/Common.cpp
        WatchySim/arduino/dtostrf.cpp
        WatchySim/arduino/String.cpp
        WatchySim/WatchFaces/Niobe/niobe.cpp
        WatchySim/WatchFaces/Scene/scene.cpp
        WatchySim/WatchFaces/7_SEG/Watchy_7_SEG.cpp
        WatchySim/WatchFaces/DOS/Watchy_DOS.cpp
        WatchySim/WatchFaces/MacPaint/Watchy_MacPaint.cpp
        WatchySim/WatchFaces/Mario/Watchy_Mario.cpp
        WatchySim/WatchFaces/Pokemon/Watchy_Pokemon.cpp
        WatchySim/WatchFaces/Tetris/Watchy_Tetris.cpp
        WatchySim/Watchy.cpp
        WatchySim/WatchySim.cpp
        WatchySim/WatchFaces/AnalogGabel/Watchy_AnalogGabel.cpp
        WatchySim/WatchFaces/DrawTest/Watchy_Draw_Test.cpp
        WatchySim/WatchFaces/PowerShell/Watchy_PowerShell.cpp
)
set(HEADERS
        WatchySim/arduino.h
        WatchySim/arduino/Common.h
        WatchySim/arduino/dtostrf.h
        WatchySim/arduino/pgmspace.h
        WatchySim/arduino/String.h
        WatchySim/config.h
        WatchySim/DSEG7_Classic_Bold_53.h
        WatchySim/framework.h
        WatchySim/FreeMonoBold9pt7b.h
        WatchySim/gfxfont.h
        WatchySim/WatchFaces/AnalogGabel/FreeSerifBold12pt7b.h
        WatchySim/WatchFaces/AnalogGabel/FreeSerifBoldItalic4pt7b.h
        WatchySim/WatchFaces/AnalogGabel/FreeSerifBoldItalic9pt7b.h
        WatchySim/WatchFaces/AnalogGabel/FreeSerifItalic9pt7b.h
        WatchySim/WatchFaces/Scene/ModernDOS8x168pt7b.h
        WatchySim/WatchFaces/Niobe/niobe.h
        WatchySim/pgmspace.h
        WatchySim/Resource.h
        WatchySim/WatchFaces/Scene/scene.h
        WatchySim/targetver.h
        WatchySim/WatchFaces/7_SEG/Watchy_7_SEG.h
        WatchySim/WatchFaces/DOS/Watchy_DOS.h
        WatchySim/WatchFaces/MacPaint/Watchy_MacPaint.h
        WatchySim/WatchFaces/Mario/Watchy_Mario.h
        WatchySim/WatchFaces/Pokemon/Watchy_Pokemon.h
        WatchySim/WatchFaces/Tetris/Watchy_Tetris.h
        WatchySim/Watchy.h
        WatchySim/WatchySim.h
        WatchySim/WatchFaces/AnalogGabel/analoggabel.h
        WatchySim/WatchFaces/AnalogGabel/Watchy_AnalogGabel.h
        WatchySim/WatchFaces/PowerShell/Watchy_PowerShell.h
        WatchySim/WatchFaces/Scene/Watchy_scene.h
)

set(RESOURCES
        WatchySim/WatchySim.rc
)
add_executable(WatchySim WIN32 ${SOURCES} ${HEADERS} ${RESOURCES})


# Specify the platform and configuration options
if (CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MDd /Zi")
    set(CMAKE_EXE_LINKER_FLAGS_DEBUG "${CMAKE_EXE_LINKER_FLAGS_DEBUG} /DEBUG")
else ()
    set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MD /O2 /Ob2 /DNDEBUG")
    set(CMAKE_EXE_LINKER_FLAGS_RELEASE "${CMAKE_EXE_LINKER_FLAGS_RELEASE} /OPT:REF /OPT:ICF")
endif ()

# Include directories
include_directories(
        ${CMAKE_SOURCE_DIR}/arduino
        ${CMAKE_SOURCE_DIR}/WatchFaces
)
target_compile_definitions(WatchySim PRIVATE WATCHY_SIM)

# Set properties and definitions
target_compile_definitions(WatchySim PRIVATE UNICODE _UNICODE)
