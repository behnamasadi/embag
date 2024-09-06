cmake_minimum_required(VERSION 3.10)
cmake_policy(SET CMP0079 NEW)

project(embag)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(Boost 1.74 COMPONENTS date_time filesystem system iostreams REQUIRED)
find_package(BZip2 REQUIRED)

include_directories(${Boost_INCLUDE_DIRS})
include_directories(${BZIP2_INCLUDE_DIR})
include_directories(lib)

file(GLOB LIB "lib/*.cc")

# Create the embag library
add_library(embag STATIC ${LIB})

# Link libraries to embag
target_link_libraries(embag PRIVATE ${Boost_LIBRARIES} ${BZIP2_LIBRARIES})

