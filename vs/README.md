# Visual Studio Property Sheets

This directory contains property sheets (configuration files) for different types of
Visual C++ projects (`.vcxproj` files).

> [!NOTE]
> All directories (except for include directories) get `$(Configuration)\` added as a suffix.


## Common Configuration
All files share the following settings:
* directory `tmp\$(ProjectName)\` for intermediate files
* compiler flag `/Zc:__cplusplus` for proper `__cplusplus` value
* C++ 20
* directory `lib\` for additional libraries




## Individual Configurations

### Quick Overview

| Filename            | Display Name        | Project type                | Output directory |
|---------------------|---------------------|-----------------------------|------------------|
| `app`               | `rlApp`             | Applications                | `bin\`           |
| `lib-dynamic`       | `rlDynamicLib`      | Dynamic libraries           | `lib\`           |
| `lib-dynamic-test`  | `rlDynamicLibTest`  | Tests for dynamic libraries | `bin\`           |
| `lib-static`        | `rlStaticLib`       | Static libraries            | `lib\`           |
| `lib-static-test`   | `rlStaticLibTest`   | Tests for static libraries  | `bin\`           |


### In Detail

#### `app`
(no additional configuration changes)

#### `lib-dynamic`
* additional include directory `$(ProjectDir)..\include` (relative for usage as git module)
* additional library directory for librarian
* post-build event: copying DLLs from `$(OutDir)` to `bin\` post-build

#### `lib-dynamic-test`
* additional include directory `$(ProjectDir)..\include` (relative for usage as git module)

#### `lib-static`
* additional include directory `$(ProjectDir)..\include` (relative for usage as git module)
* additional library directory for librarian

#### `lib-static-test`
* additional include directory `$(ProjectDir)..\include` (relative for usage as git module)
