
cmake_minimum_required(VERSION 3.14)


project(features_mysql)

set(CMAKE_CXX_STANDARD 17)

# First, import trpc-cpp.
include(FetchContent)
FetchContent_Declare(
    trpc-cpp
    GIT_REPOSITORY    https://github.com/KosmosFult/trpc-cpp.git
    GIT_TAG           mysql-main-repo
    SOURCE_DIR        ${CMAKE_CURRENT_SOURCE_DIR}/cmake_third_party/trpc-cpp
)
FetchContent_MakeAvailable(trpc-cpp)

# Then, import cpp-telemetry-opentelemetry
FetchContent_Declare(
    trpc_cpp_database_mysql
    GIT_REPOSITORY    https://github.com/KosmosFult/cpp-database-mysql.git
    GIT_TAG           main
    SOURCE_DIR        ${CMAKE_CURRENT_SOURCE_DIR}/cmake_third_party/trpc_cpp_database_mysql
)
FetchContent_MakeAvailable(trpc_cpp_database_mysql)



# compile client
file(GLOB SRC_FILES ${CMAKE_CURRENT_SOURCE_DIR}/client/fiber/*.cc)
add_executable(fiber_client ${SRC_FILES})
target_link_libraries(fiber_client trpc trpc_cpp_database_mysql)

file(GLOB SRC_FILES ${CMAKE_CURRENT_SOURCE_DIR}/client/future/*.cc)
add_executable(future_client ${SRC_FILES})
target_link_libraries(future_client trpc trpc_cpp_database_mysql)