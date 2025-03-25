cmake_minimum_required(VERSION 3.10)

# Project name and C++ standard
project(HFT_WebSocket)
set(CMAKE_CXX_STANDARD 17)

# Specify the path where Boost is installed (use forward slashes)
set(BOOST_ROOT "/mnt/c/Users/ADMIN/GoQuantAssignment/WebSocket_HFT/boost_1_87_0/boost_1_87_0")

# Find required packages
find_package(Boost REQUIRED)
find_package(OpenSSL REQUIRED)

# Add WebSocketPP include directory (use forward slashes)
include_directories("/mnt/c/Users/ADMIN/GoQuantAssignment/WebSocket_HFT/websocketpp")

include_directories(/usr/include/x86_64-linux-gnu)


# Add the executable and source files
add_executable(deribit_trader
    deribit_trader.cpp
    websocket_handler.cpp
    trade_execution.cpp
    latency_module.cpp
)

# Specify the directory for the executable to be placed
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Include Boost in your project
target_include_directories(deribit_trader PRIVATE ${Boost_INCLUDE_DIRS})

# Link Boost and OpenSSL libraries
target_link_libraries(deribit_trader PRIVATE ${Boost_LIBRARIES} OpenSSL::SSL)

