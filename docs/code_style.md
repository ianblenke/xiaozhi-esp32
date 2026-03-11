# Code Style Guide

## Code Formatting Tool

This project uses the clang-format tool to unify code style. We have provided a `.clang-format` configuration file in the project root directory, based on the Google C++ style guide with some custom adjustments.

### Installing clang-format

Before using it, please make sure you have installed the clang-format tool:

- **Windows**:
  ```powershell
  winget install LLVM
  # Or use Chocolatey
  choco install llvm
  ```

- **Linux**:
  ```bash
  sudo apt install clang-format  # Ubuntu/Debian
  sudo dnf install clang-tools-extra  # Fedora
  ```

- **macOS**:
  ```bash
  brew install clang-format
  ```

### Usage

1. **Format a single file**:
   ```bash
   clang-format -i path/to/your/file.cpp
   ```

2. **Format the entire project**:
   ```bash
   # Run in the project root directory
   find main -iname *.h -o -iname *.cc | xargs clang-format -i
   ```

3. **Check formatting before committing code**:
   ```bash
   # Check if the file format meets the standard (does not modify the file)
   clang-format --dry-run -Werror path/to/your/file.cpp
   ```

### IDE Integration

- **Visual Studio Code**:
  1. Install the C/C++ extension
  2. In settings, set `C_Cpp.formatting` to `clang-format`
  3. You can enable auto-format on save: `editor.formatOnSave: true`

- **CLion**:
  1. In settings, navigate to `Editor > Code Style > C/C++`
  2. Set `Formatter` to `clang-format`
  3. Select to use the `.clang-format` configuration file in the project

### Main Formatting Rules

- Indentation uses 4 spaces
- Line width limit is 100 characters
- Braces use the Attach style (on the same line as the control statement)
- Pointer and reference symbols are left-aligned
- Auto-sorting of header file includes
- Class access modifier indentation is -4 spaces

### Notes

1. Please ensure code is formatted before committing
2. Do not manually adjust alignment of already formatted code
3. If you do not want a section of code to be formatted, you can surround it with the following comments:
   ```cpp
   // clang-format off
   // Your code
   // clang-format on
   ```

### FAQ

1. **Formatting fails**:
   - Check if the clang-format version is too old
   - Confirm the file encoding is UTF-8
   - Verify the .clang-format file syntax is correct

2. **Format does not match expectations**:
   - Check if you are using the .clang-format configuration from the project root directory
   - Confirm that no .clang-format file in another location is being used with higher priority

If you have any questions or suggestions, feel free to submit an issue or pull request.
