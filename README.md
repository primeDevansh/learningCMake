# Learning CMake

### What is CMake?

CMake is an open-source, cross-platform family of tools designed to build, test, and package software. The primary purpose of CMake is to control the compilation process of software using simple platform and compiler-independent configuration files.

### Why Use CMake?

1. **Portability**: CMake makes it easy to build your software on different platforms (Windows, macOS, Linux, etc.) and with different compilers (GCC, Clang, MSVC, etc.).
2. **Flexibility**: It supports complex build processes and can be integrated with various build systems (like Make, Ninja, Xcode, Visual Studio).
3. **Ease of Use**: Once set up, it simplifies the build process, making it easier to manage dependencies, include external libraries, and configure project settings.

### Basic Concepts

- **CMakeLists.txt**: The configuration file used by CMake to determine how to build your project. This file contains CMake commands to specify the project's source files, required libraries, and build options.
- **Source Directory**: The directory containing your `CMakeLists.txt` file and source code.
- **Build Directory**: The directory where the build files (makefiles, project files, etc.) and compiled binaries will be generated.

### Basic CMake Workflow

1. **Write a `CMakeLists.txt` file**: This file describes the configuration and rules for building your project.
2. **Run CMake**: Use CMake to generate build files for your chosen build system.
3. **Build the Project**: Use the generated build files to compile your project.

### Getting Started with CMake

Let's walk through a simple example to build a basic C++ project.

#### Example Project Structure

```css
MyProject/
├── src/
│   └── main.cpp
└── CMakeLists.txt
```

#### Step-by-Step Guide

1. **Create the Source Directory and Source File**

Create a directory for your project (`MyProject`) and a source file (`main.cpp`) with the following content:

```cpp
// src/main.cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

2. **Write the `CMakeLists.txt` File**

Create a `CMakeLists.txt` file in the `MyProject` directory with the following content:

```cmake
# Specify the minimum version of CMake required
cmake_minimum_required(VERSION 3.10)

# Set the project name
project(MyProject)

# Add an executable target
add_executable(MyProject src/main.cpp)
```

3. **Generate Build Files**

Open a terminal and navigate to the `MyProject` directory. Create a build directory and run CMake:

```sh
mkdir build
cd build
cmake ..
```

This command generates the necessary build files in the `build` directory. The `..` tells CMake to look for the `CMakeLists.txt` file in the parent directory.

4. **Build the Project**

Still in the `build` directory, compile the project using the generated build files. For example, if CMake generated a Makefile, you can run:

```sh
make
```

This will compile the `main.cpp` file and produce an executable named `MyProject` in the `build` directory.

5. **Run the Executable**

```sh
./MyProject
```

This should output:

```
Hello, World!
```

### Advanced CMake Features

CMake offers a lot more features, such as:

- **Library Management**: Linking external libraries.
- **Configuration Management**: Handling different build configurations (Debug, Release).
- **Testing**: Integrating with testing frameworks (like CTest).
- **Packaging**: Creating installers or packages.

Here’s a brief example demonstrating some advanced features:

```cmake
cmake_minimum_required(VERSION 3.10)
project(MyProject VERSION 1.0)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add the executable
add_executable(MyProject src/main.cpp)

# Find and link an external library (example: Boost)
find_package(Boost 1.60 REQUIRED COMPONENTS system)
if(Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
    target_link_libraries(MyProject ${Boost_LIBRARIES})
endif()

# Enable testing
enable_testing()
add_test(NAME MyProjectTest COMMAND MyProject)
```

### Conclusion

CMake is a powerful tool for managing the build process of software projects, particularly for those requiring cross-platform support. By writing a `CMakeLists.txt` file, you can define the structure and dependencies of your project, and CMake will handle the generation of the necessary build files. With a little practice, you'll find that CMake significantly simplifies the process of building complex projects.

1. To generate build files:

    ```sh
    mkdir build
    cd build
    cmake ..
    ```

    This command generates the necessary build files in the build directory. The .. tells CMake to look for the CMakeLists.txt file in the parent directory.