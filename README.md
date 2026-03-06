# EzLogger
---

<div align="center">

![C++20](https://img.shields.io/badge/C%2B%2B-20-blue.svg?style=for-the-badge&logo=cplusplus)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
![Thread-safe](https://img.shields.io/badge/thread--safe-yes-brightgreen.svg?style=for-the-badge)
![Header-only](https://img.shields.io/badge/header--only-yes-brightgreen.svg?style=for-the-badge)
![Dependencies](https://img.shields.io/badge/dependencies-ZERO-success.svg?style=for-the-badge)
![Single File](https://img.shields.io/badge/📄%20single%20file-logger.h-brightgreen.svg?style=for-the-badge)
</div>

Ezlogger (easy logger): Easy, lightweight, header-only, synchronous, thread-safe, modern C++20 file logger. Ez is designed to be easy to drop into any project. It uses `std::source_location` to automatically capture file, function, and line information without traditional macros. Perfect for small to medium C++20 projects that need logging without complexity.

## Features

- Lightweight, header-only, no external dependencies. Literally 1 single header file of ~200 LOC
- Synchronous Thread-safe (mutex + atomic)
- Configurable log levels: TRACE, DEBUG, INFO, WARNING, ERROR
- Automatic capture of function, file, and line via `std::source_location`

## Installation

**Literally one step:**

1. Copy `logger.h` to your project

That's it. No build scripts, no CMake, no package managers.

```cpp
#include "logger.h"  // You're done!
```

## Example usage
```cpp
#include "logger.h"

int main() {
    if (auto err = setLogFile("app.log")) {
        std::cerr << *err << '\n';
        return 1;
    }

    // Set log level (optional, default is INFO)
    setDebugLogLevel();

    // Log messages
    LOG_INFO("Application started");
    int x = 42;
    LOG_DEBUG("Value of x: " + std::to_string(x));
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
## Contributing

Contributions are welcome! Feel free to:
- Open issues for bugs or feature requests
- Submit pull requests
- Suggest improvements

## License
MIT License - see [LICENSE](LICENSE) file for details.

## Version

* **Current version**: 1.0.0 (March 2026)

See [CHANGELOG.md](CHANGELOG.md) for release history.

---
<div align="center">

**If you find this useful, consider giving it a ⭐!**

</div>
