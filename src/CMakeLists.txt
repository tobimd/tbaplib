# Optional header statement for IDEs
set(HEADER_LIST "${tbap_SOURCE_DIR}/include/tbap/*")

# Make automatic shared library
add_library(tbap SHARED main.cpp ${HEADER_LIST})

# Specify needed directories
target_include_directories(
    tbap 
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:../include>
)

# Users need at least C++17
target_compile_features(tbap PUBLIC cxx_std_17)

# Specify where to put headers for IDEs
source_group(
    TREE "${PROJECT_SOURCE_DIR}/include"
    PREFIX "Header Files"
    FILES ${HEADER_LIST})
