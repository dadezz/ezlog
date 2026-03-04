# EzLogger
Easy, lightweight, header-only, thread-safe, C++20 file logger.

Ez is a **header-only**, thread-safe, modern C++20 logger designed to be easy to drop into any project.  
It uses `std::source_location` to automatically capture file, function, and line information without traditional macros.

## Features

- Header-only, no external dependencies
- Thread-safe (mutex + atomic)
- Configurable log levels: TRACE, DEBUG, INFO, WARNING, ERROR
- Automatic capture of function, file, and line via `std::source_location`

## Installation
Simply copy `logger.h` into your project include folder (e.g., `include/`) and include it:
```cpp
#include "logger.h"
```
## Example usage
```cpp
#include "logger.h"

int main() {
    if (auto err = setLogFile("app.log")) {
        return *err;
    }

    // Set log level (optional, default is INFO)
    setDebugLogLevel();

    // Log messages
    LOG_INFO("Application started");
    LOG_DEBUG("Value of x: 42");
    LOG_ERROR("Critical error occurred");

    // Close log file (optional, RAII handles it)
    closeLogFile();
    return 0;
}
```

## Output example
```
[2026-02-03 09:49:55]	[INF]	[main]	(\proj\main.cpp:390)	Mode: SOLVE ONLY
[2026-02-03 09:50:02]	[ERR]	[ReadSourceWithOffsets]	(\proj\main.cpp:255)	Error reading source data (EOF or format mismatch)
[2026-02-03 09:51:35]	[INF]	[main]	(\proj\main.cpp:390)	Mode: SOLVE ONLY
[2026-02-03 09:52:13]	[TRA]	[RemoveBoundaryPoints]	(\proj\main.cpp:90)	Cleaning BBox detected: X[-22.610047, 78.296342]
[2026-02-03 09:52:13]	[TRA]	[RemoveBoundaryPoints]	(\proj\main.cpp:91)	Cleaning BBox detected: Y[4.897534, 34.994043]
[2026-02-03 09:52:13]	[TRA]	[RemoveBoundaryPoints]	(\proj\main.cpp:92)	Cleaning BBox detected: Z[-24.498014, 26.145680]
[2026-02-03 09:52:13]	[DEB]	[RemoveBoundaryPoints]	(\proj\main.cpp:130)	BBox Clean: Removed 3058 b-points. Remaining: 1775949
```
