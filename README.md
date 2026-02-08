# OpenGL C++ Project with vcpkg

This is a C++ template project for OpenGL development with automatic dependency management using vcpkg.

## Prerequisites

Before running the cmake configuration command, ensure you have:

1. **CMake** (version 3.23 or higher) - [Download](https://cmake.org/download/)
2. **Visual Studio 2022** or another supported C++ compiler
3. **vcpkg** - For dependency management
   - Clone vcpkg: `git clone https://github.com/Microsoft/vcpkg.git`
   - Or set `VCPKG_ROOT` environment variable to your vcpkg installation

## Building the Project

### Step 1: Configure with CMake

Run the following command from the project root directory:

```bash
cmake -S . -B build --preset=default
```

#### Command Explanation

- **`cmake`** - The CMake build system generator
- **`-S .`** - Specifies the source directory (current directory `.`)
- **`-B build`** - Specifies the build directory as `build/` (where generated files will be placed)
- **`--preset=default`** - Uses the `default` configuration preset from `CMakePresets.json`

### What This Command Does

1. Scans the `CMakeLists.txt` file to understand the project structure
2. Looks for required packages (glfw3, imgui, Eigen3, etc.) via vcpkg
3. Generates build system files in the `build/` directory
4. Sets up the build environment with proper compiler settings and C++17 standard

### Step 2: Build the Project

After successful cmake configuration, build the project:

```bash
cmake --build build --config Release
```

Or for debug builds:

```bash
cmake --build build --config Debug
```

## Project Structure

```
.
├── CMakeLists.txt              # Main CMake configuration
├── CMakePresets.json           # CMake build presets
├── CMakeUserPresets.json       # User-specific presets (optional)
├── vcpkg.json                  # vcpkg manifest for dependencies
├── vcpkg-configuration.json    # vcpkg configuration
├── src/
│   └── main.cpp               # Main entry point
└── build/                      # Generated build files (created by cmake)
```

## Available Presets

The following presets are available in `CMakePresets.json`:

- **`default`** - Default configuration (recommended)
- **`Debug`** - Debug build with debugging symbols
- **`Release`** - Release build optimized for performance
- **`configure-vs2022`** - Visual Studio 2022 generator
- **`configure-xcode`** - Xcode generator (for macOS)

## Environment Variables

If using the standalone vcpkg preset, set:

```bash
$env:VCPKG_ROOT = "path/to/vcpkg"  # PowerShell
# or
set VCPKG_ROOT=path\to\vcpkg       # Command Prompt
```

## Dependencies

The project uses the following dependencies (managed via vcpkg):

- **glfw3** - Window and input handling
- **imgui** - GUI user interface
- **Eigen3** - Linear algebra library
- **nfd** - Native file dialogs
- **fmt** - String formatting
- **OpenGL** - Graphics API
- **implot** - Plotting library
- **lodepng** - PNG image loading
- **nlohmann_json** - JSON parsing
- **argparse** - Command-line argument parsing
- **tinyobjloader** - OBJ model loading
- **OpenMP** (optional) - Parallel computing
- **im3d** (optional) - 3D immediate mode graphics

## Troubleshooting

### CMake not found
- Ensure CMake is installed and in your PATH
- Restart your terminal or IDE after installation

### Preset not found
- Check that `CMakePresets.json` is in the project root
- Verify the preset name matches exactly

### Package not found errors
- Ensure vcpkg is properly installed
- Set the `VCPKG_ROOT` environment variable correctly
- Run `vcpkg install --triplet x64-windows-static` to install dependencies

### Build errors
- Check that you're using C++ compiler compatible with C++17
- Ensure all dependencies are properly installed via vcpkg

## Next Steps

Once the build completes successfully:

1. Open the generated solution file (`.sln` for Visual Studio)
2. Run the executable from the `build/` directory
3. Modify `src/main.cpp` to add your OpenGL code

## Additional Resources

- [CMake Documentation](https://cmake.org/documentation/)
- [vcpkg Documentation](https://vcpkg.io/)
- [CMakePresets Documentation](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html)
