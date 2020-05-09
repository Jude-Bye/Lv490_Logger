cmake_minimum_required(VERSION 3.16)
project(LoggerLibrary)

set(CMAKE_CXX_STANDARD 17)

if (CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(OutputFile LoggerLibrary-d)
    message("Debug filename: " "${OutputFile}")
else()
    set(OutputFile LoggerLibrary)
    message("Default filename: " "${OutputFile}")
endif ()

add_library("${OutputFile}" SHARED src/library.cpp src/library.h
        src/Essentials/LogFundamentals.h
        src/Filelogger/filelogger.h
        src/filelogger_Messages.h
        src/filelogger_StreamModes.h

        src/LogFundamentals.cpp
        src/filelogger.cpp
        src/filelogger_FileManager.cpp
        src/filelogger_Messages.cpp
        src/filelogger_StreamModes.cpp

        src/ILogger.h
        src/LoggerDLL.h
        src/Filelogger/FileLogAdapters.h
        src/StaticLogging.h
        src/Essentials/ExportConfig.h
        src/ConcQueue.h
        )

target_link_libraries("${OutputFile}"
        PUBLIC stdc++fs
        PUBLIC -pthread)
