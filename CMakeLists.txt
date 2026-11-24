cmake_minimum_required(VERSION 3.16)
project(StudentCourseRegistration LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(SQLITE_AMALGAMATION_C "${CMAKE_CURRENT_SOURCE_DIR}/sqlite/sqlite3.c")
set(SQLITE_AMALGAMATION_DIR "${CMAKE_CURRENT_SOURCE_DIR}/sqlite")

if(EXISTS "${SQLITE_AMALGAMATION_C}")
    # Admin executable
    add_executable(admin_app
        Admin/main.cpp
        "${SQLITE_AMALGAMATION_C}"
    )
    target_include_directories(admin_app PRIVATE
        "${SQLITE_AMALGAMATION_DIR}"
        Admin
    )

    # Student executable
    add_executable(student_app
        Student/main.cpp
        "${SQLITE_AMALGAMATION_C}"
    )
    target_include_directories(student_app PRIVATE
        "${SQLITE_AMALGAMATION_DIR}"
        Student
    )

    # Threading / dl libraries on Unix-like systems
    if(UNIX AND NOT APPLE)
        target_link_libraries(admin_app PRIVATE pthread dl)
        target_link_libraries(student_app PRIVATE pthread dl)
    endif()
else()
    message(FATAL_ERROR
        "SQLite amalgamation not found at ${SQLITE_AMALGAMATION_C}. "
        "Place sqlite3.c and sqlite3.h in ./sqlite/ or switch to Option 2."
    )
endif()