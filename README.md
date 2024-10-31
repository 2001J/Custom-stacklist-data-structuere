# Custom Stacklist Data Structure

This project implements a custom stacklist data structure in C. It uses a custom library called `birchutils` for additional utilities.

## Features

- **Creation of a Stacklist**: Function to create and initialize a new stacklist.
- **Finding the Last Element**: Function to find the last element in the stacklist.
- **Finding the Penultimate Element**: Function to find the second-to-last element in the stacklist.
- **Push Operation**: Function to add a new element to the end of the stacklist.
- **Pop Operation**: Function to remove and return the last element from the stacklist.
- Utility functions from `birchutils`.

## Prerequisites

- GCC (GNU Compiler Collection)
- Make

## Installing `birchutils`

Before building the `stacklist` project, you need to install the `birchutils` library. Follow these steps:

1. Download the `birchutils` library from the official website:
   [Download birchutils v1.1](https://repo.doctorbirch.com/birchutils/v1.1/)

2. Extract the downloaded archive and navigate to the `birchutils` directory:
   ```sh
   tar -xzf birchutils-v1.1.tar.gz
   cd birchutils
   ```

3. Modify the `Makefile` to include the `libdir`, `incdir`, and `install` target:
   ```makefile
   flags = -O3 -Wall -std=c2x
   ldflags = -fPIC -shared -ldl -D_GNU_SOURCE
   
   # Add these lines to specify the library and include directories
   libdir = /usr/local/lib
   incdir = /usr/local/include
   
   all: clean birchutils.so
   
   birchutils.so: birchutils.o
   cc $(flags) $^ -o $@ $(ldflags)
   
   birchutils.o: birchutils.c
   cc $(flags) -c $^
   
   clean:
   rm -f birchutils.o birchutils.so
   
   # Add this install target
   install: birchutils.so
   cp birchutils.so $(libdir)/libbu.so
   cp birchutils.h $(incdir)
   # For macOS
   install_name_tool -id $(libdir)/libbu.so $(libdir)/libbu.so
   # For Linux, you might need to run ldconfig instead
   # ldconfig
   ```
   - For Linux: The default values should work, but you may need to use ldconfig instead of install_name_tool.
   - For macOS: The provided Makefile should work as is.
   - For Windows: You may need to use a different build system (e.g., CMake) or adjust the paths accordingly.

4. Build and install the `birchutils`:
   ```sh
   make
   sudo make install
    ```

## Building the stacklist Project

1. Clone the stacklist repository:
   ```sh
   git clone <stacklist-repo-url>
   cd stacklist
   ```

2. Build the project:
   ```sh
   make
   ```

## Running the stacklist Program

To run the stacklist program, use the following command:
   ```sh
   ./stacklist
   ```

## License

This project is licensed under the MIT License.

## Acknowledgments

This project uses the `birchutils` library developed by [Doctor Birch](https://doctorbirch.com).

## Author

Joseph Paul Koyi
