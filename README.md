
## 42 Get Next Line README.md

# 42 Get Next Line

Get Next Line is a project focused on creating a robust function to read a line from a file descriptor until a newline or EOF is encountered. This project enhances your understanding of file I/O in C along with dynamic memory management.

## Features

- **Buffered Reading:** Efficiently reads files using a configurable buffer.  
- **Line-by-Line Output:** Returns a complete line each time the function is called.  
- **Multi-File Handling:** (Bonus) Supports reading from multiple file descriptors concurrently.

## Mandatory
- **Works with one file descriptor by reading file line by line**

## Bonus
- **Works with two pr more file descriptor at the same time by reading files line by line**

## Installation

Clone the repository (bash):
```
git clone https://github.com/RubBarkhudaryan/42-Get-Next-Line.git
```

## Compile the library:

```
make
```

## Usage
Include the header file in your project:

```
#include "get_next_line.h"
```

## Example usage
```
int  fd = open("text.txt", RD_ONLY);
ft_printf("line: %s", get_next_line(fd));
```

## Project Structure

**get_next_line_utils.c** – utilities for correct functionality of get_next_line

**get_next_line.c** - the main part of get_next_line implementation

**get_next_line.h** - header file where were defined all the neccessary functions and macros

**Author
Rub Barkhudaryan**
