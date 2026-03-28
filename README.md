# 42 Get Next Line

## Overview
Get Next Line implements a function that returns one full line per call from a file descriptor.

It is designed to handle partial reads, internal buffering, and dynamic line assembly.

The challenge is not just reading a file. It is preserving read state across calls while returning exactly one line at a time with clean memory behavior.

## Features
- Buffered reads with configurable buffer size
- Returns one line at a time
- Handles end-of-file correctly
- Prevents memory leaks across repeated calls
- Bonus support for multiple file descriptors simultaneously

## Core Concepts

### Persistent State Between Calls
One call may stop in the middle of a buffer. The leftover data must be preserved and reused on the next call.

### Dynamic Line Assembly
Lines can be longer than BUFFER_SIZE, so the function appends chunks until a newline or EOF is reached.

### EOF and Final Line Handling
Correct behavior at EOF is subtle:
- return remaining buffered content if non-empty
- then return NULL on subsequent calls

### Bonus Multi-FD Strategy
Bonus mode tracks independent leftovers per file descriptor so simultaneous streams do not corrupt each other.

## Build
Mandatory:
- cc -Wall -Wextra -Werror get_next_line.c get_next_line_utils.c

Bonus:
- cc -Wall -Wextra -Werror get_next_line_bonus.c get_next_line_utils_bonus.c

## Usage
Include:
- get_next_line.h
or
- get_next_line_bonus.h

Call:
- get_next_line(fd)

Behavior contract:
- Returns next line including trailing newline when present
- Returns last line without newline if file ends
- Returns NULL on end or unrecoverable error

## Files
- get_next_line.c: core line-reading logic
- get_next_line_utils.c: helper functions
- get_next_line_bonus.c: multi-FD implementation

Common helper responsibilities:
- string join/slice utilities
- newline detection
- leftover extraction and update

## Key Learnings
- Stateful file reading
- Heap-based string assembly
- Edge-case management for files, stdin, and EOF

## Notes
Get Next Line is a foundational exercise in memory-safe incremental parsing.
