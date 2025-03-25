# Trading Application (Deribit_Trading)

This project is a trading application that connects to a cryptocurrency exchange via WebSockets and allows the user to place, 
cancel, modify orders, fetch order books, and view current positions. The application has been optimized for performance, including 
asynchronous network communication, memory management improvements, and threading optimizations.

## Features

- **WebSocket-based Trading Interface**: Establishes a WebSocket connection with the exchange for real-time data and trade execution.
- **Command-line Trading Operations**: Provides a user-friendly menu-driven command-line interface for trading tasks.
- **Support for Various Order Types**: Place market, limit, or other types of orders as supported by the exchange.
- **API Authentication**: Secure authentication using client credentials for accessing trading features.
- **Open Orders Management**: View and manage all active orders.
- **Order Modification and Cancellation**: Modify or cancel existing orders seamlessly.
- **Optimized Performance**: Asynchronous operations, memory management enhancements, and threading optimizations for better responsiveness.

## Project Structure

The project follows a modular structure to ensure readability, maintainability, and scalability. Here's a breakdown of the main files and their purposes:

### Modular Breakdown

1. **Main Entry Point**:
   - **`deribit_trader.cpp`**: 
     - Contains the main trading loop.
     - Implements menu-driven command-line operations.
     - Integrates all modules for a seamless trading experience.

2. **WebSocket Handling**:
   - **`websocket_handler.h`** / **`websocket_handler.cpp`**:
     - Manages WebSocket connections.
     - Sends and receives messages from the exchange in real time.
     - Handles connection errors and reconnections.

3. **Trade Execution**:
   - **`trade_execution.h`** / **`trade_execution.cpp`**:
     - Authenticates with the exchange using API credentials.
     - Places, modifies, and cancels orders.
     - Fetches current positions and order book data.

4. **Latency Measurement**:
   - **`latency_module.h`** / **`latency_module.cpp`**:
     - Provides utilities for measuring latency of critical operations.
     - Logs performance data to help optimize execution times.

5. **API Credentials**:
   - **`api_credentials.h`**:
     - Stores API client ID and secret securely.
     - Ensures credentials are modularized for easy updates without affecting other files.

### Example Workflow

- The **main program** in `deribit_trader.cpp`:
  - Initializes the WebSocket connection using `websocket_handler`.
  - Authenticates using `trade_execution`.
  - Enters a command loop to handle user inputs for placing, modifying, or canceling orders.

- The **WebSocket handler**:
  - Establishes a secure connection to the exchange.
  - Sends and receives JSON-formatted messages.

- The **trade execution module**:
  - Interacts with the exchange API for order-related operations.
  - Utilizes WebSocket messages to fetch data.

- The **latency module**:
  - Logs timestamps to measure the time taken by each operation.
  - Ensures the application meets performance requirements.

This structure ensures that individual modules can be independently developed and tested while maintaining a clear separation of concerns.

## Prerequisites

### System Requirements

- **C++ Compiler**: A compiler with C++17 support, such as:
  - GCC 7+ (Linux)
  - Clang 7+ (Linux/macOS)
  - MSVC 2017+ (Windows)
- **CMake**: Version 3.x or higher.
- **Boost Libraries**: Required for utilities like `boost::asio` for network communication.
- **OpenSSL**: For secure WebSocket and API communication.
- **Git**: For version control and cloning the repository.

### Dependencies

- `nlohmann/json` (for JSON parsing and handling)
- WebSocket library
- Boost Libraries (including `boost::asio`)



# Build the project with CMake:
a) Create a build directory:
```bash
mkdir build
cd build
```
b) Run CMake to configure the project:
```bash
cmake ..
```

c) Compile the project:
```bash
cmake --build . --config debug
```
This will generate the executable file deribit_trader.exe

# Run the application:
```bash
./deribit_trader.exe
```

## Usage
Once the application is running, you will be prompted with a menu for selecting trading operations:

mathematica
```bash
--- Trading Menu ---
1. Place Order
2. Cancel Order
3. Modify Order
4. Get Order Book
5. View Current Positions
6. Exit
```
Example Workflow
1. Place Order:

Select option 1 and input the instrument name (e.g., BTC-PERPETUAL), amount, and price.
The application will asynchronously place a buy order and show the response.

2. Cancel Order:

Select option 2 and input the order ID to cancel the order.
The application will asynchronously cancel the order and show the response.

3. Modify Order:

Select option 3 and input the order ID, new amount, and new price to modify the existing order.

4. Get Order Book:

Select option 4 and input the instrument name to view the order book.

5. View Current Positions:

Select option 5 to view the current positions in your account.

6. Exit:

Select option 6 to exit the application.






















