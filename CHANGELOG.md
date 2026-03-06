# Changelog

All notable changes to EzLogger will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-03-06

### Added
- Initial release
- Header-only, single-file logger implementation
- C++20 std::source_location support (no preprocessor macros)
- Thread-safe logging with mutex and atomic operations
- Five configurable log levels: TRACE, DEBUG, INFO, WARNING, ERROR
- Automatic timestamp formatting
- Automatic file, function, and line number capture
- Cross-platform timestamp support (Windows/POSIX)
- RAII-based file management
- MIT License

### Features
- ~200 lines of code
- Zero external dependencies
- Meyer's singleton pattern
- Smart path and function name extraction for cleaner output

[1.0.0]: https://github.com/dadezz/EzLogger/releases/tag/v1.0.0
