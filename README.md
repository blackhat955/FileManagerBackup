# FileManagerBackup

## Overview

The `FileManagerBackup` project provides a set of utilities to manage file backups and search for files within a directory. The primary functionalities include:

- **Backing up directories**: Recursively copies files from a source directory to a destination directory.
- **Searching for files**: Allows searching for files within a directory based on a search term.

The project is implemented in C++17 and uses the `std::filesystem` library for handling file system operations.

## Features

- **Backup Directory**: Copy all files and subdirectories from the source directory to the destination directory.
- **Search Files**: Search for files in a given directory and its subdirectories based on a search term.

## Requirements

- **C++17**: The project requires a C++17 compatible compiler (e.g., GCC 9.0+ or Clang 8+).
- **CMake**: CMake 3.10 or higher for building the project.
- **Filesystem Support**: The project uses the `std::filesystem` library, which is available from C++17 onwards.

## Build Instructions

### Prerequisites

Ensure you have the following installed:
- A C++17 compatible compiler (e.g., GCC 9.0+, Clang 8+).
- CMake 3.10 or higher.

### Steps to Build the Project

1. Clone the repository:

    ```bash
    git clone https://github.com/your-username/FileManagerBackup.git
    cd FileManagerBackup
    ```

2. Create a build directory and configure the project using CMake:

    ```bash
    mkdir build
    cd build
    cmake ..
    ```

3. Build the project using `make`:

    ```bash
    make
    ```

4. The resulting executable will be created in the `build` directory as `FileManagerBackup`.

### Compiler and Filesystem Setup

- If you're using GCC version **8.0 or below**, you may need to link the filesystem library manually by adding the following line to your `CMakeLists.txt`:

    ```cmake
    target_link_libraries(FileManagerBackup stdc++fs)
    ```

    This is no longer required for GCC 9.0+ or Clang.

- For Clang, no extra configuration is necessary, but ensure you're using the correct C++ standard library:

    ```cmake
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++")
    ```

## Usage

### Backing Up a Directory

The `FileManager::backupDirectory` function allows you to copy all files and subdirectories from a source directory to a destination directory. Here's an example of how to use it:

```cpp
#include "FileManager.h"

int main() {
    FileManager fileManager;
    try {
        fileManager.backupDirectory("/path/to/source", "/path/to/destination");
        std::cout << "Backup completed successfully." << std::endl;
    } catch (const std::exception& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }
    return 0;
}
