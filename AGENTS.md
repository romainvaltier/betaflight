# Betaflight Agent Guidelines

## Build Commands
- `make TARGET=<target>` - Build firmware for specific target
- `make all` - Build all targets (CI targets)
- `make preview` - Build one target per platform and run tests
- `make clean` - Clean build artifacts
- `make clean_all` - Clean all build artifacts including tests

## Lint/Static Analysis Commands
- `make cppcheck` - Run static analysis on C source code
- `make test` - Run unit tests (default)
- `make test-all` - Run all unit tests (including per-target expanded tests)
- `make test-representative` - Run a representative subset of tests
- `make junittest` - Run unit tests with JUnit XML output

## Running Specific Tests
To run a specific test:
- `make test_<test_name>` - Run a single test (e.g., `make test_maths_unittest`)
- `cd src/test && make test_<test_name>` - Alternative method

## Code Style Guidelines

### General
- C language with GNU extensions
- Follow existing code style in the repository
- Use 4-space indentation (no tabs)
- Function names use snake_case (e.g., `calculate_value`)
- Variable names use snake_case (e.g., `max_value`)
- Constants use UPPER_CASE (e.g., `MAX_SIZE`)
- Struct/union/enum names use PascalCase with suffixes:
  - `_s` for structs (e.g., `motor_config_s`)
  - `_u` for unions (e.g., `data_union_u`)
  - `_e` for enums (e.g., `state_e`)

### Headers
- Include guards use `#pragma once`
- Header files should be self-contained where possible
- Include order: system headers, then local headers, then project headers

### Functions
- Function parameters use snake_case naming
- Function names are prefixed with module name (e.g., `fc_set_arm_state`)
- Functions should be small and focused on single responsibilities
- All functions have proper documentation comments

### Error Handling
- Use `return` for early exits from functions
- Return error codes or boolean values to indicate success/failure
- Avoid using `exit()` or `abort()`

### Naming Conventions
- Global variables use `g_` prefix (e.g., `g_system_state`)
- Static variables use `s_` prefix (e.g., `s_internal_counter`)
- Local variables should be descriptive and short
- Boolean variables should be prefixed with `is_`, `has_`, or `can_`

### Comments
- Use `//` for single-line comments in C code
- Use `/* */` for multi-line comments
- Add Doxygen-style comments for public APIs
- Avoid excessive inline comments; prefer descriptive naming over comments

### Formatting
- All source files should end with a newline character
- No trailing whitespace on lines
- Use spaces around operators (`=`, `+`, `-`, etc.)
- Space after commas in function calls and declarations
- No space before opening parenthesis in function calls

### Includes
- Include standard C library headers first
- Then include system headers
- Finally include project-specific headers
- Sort includes alphabetically within each group