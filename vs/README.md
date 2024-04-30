# Visual Studio Property Sheets

This directory contains property sheets (configuration files) for different types of
Visual C++ projects (`.vcxproj` files).

> [!NOTE]
> All directories (except for include directories) get `$(Configuration)\` added as a suffix.


## File System
The following directory structure is assumed:
```
<repo root>
 ├ <solution file>
 ├───bin
 │   ├───Debug
 │   │   └─── <debug versions of executables (.exe, .pdb)>
 │   └───Release
 │       └─── <release versions of executables (.exe, .pdb)>
 ├───dependencies
 │   └─── <submodules>
 ├───examples
 │   └─── <directories containing examples, project file on highest level within>
 ├───include
 │   └─── <include subdirectories, like "rlText">
 ├───lib
 │   ├───Debug
 │   │   └─── <debug versions of libraries (.exp, .lib, .idb, .pdb)>
 │   └───Release
 │       └─── <release versions of libraries (.exp, .lib, .pdb)>
 ├───src
 │   └─── <source files + private headers>
 ├───test
 │   └─── <directories containing tests, project file on highest level within>
 └───tmp
     └─── <intermediate files>
```


## Common Configuration
All files share the following settings:
* directory `tmp\$(ProjectName)\` for intermediate files
* compiler flag `/Zc:__cplusplus` for proper `__cplusplus` value
* C++ 20
* directory `lib\` for additional libraries




## Individual Configurations

### Quick Overview

| Filename          | Display Name      | Project type                         | Output directory |
|-------------------|-------------------|--------------------------------------|------------------|
| `app`             | `rlApp`           | Applications                         | `bin\`           |
| `lib-dynamic`     | `rlDynamicLib`    | Dynamic libraries                    | `lib\`           |
| `lib-dynamic-app` | `rlDynamicLibApp` | Tests/examples for dynamic libraries | `bin\`           |
| `lib-static`      | `rlStaticLib`     | Static libraries                     | `lib\`           |
| `lib-static-app`  | `rlStaticLibApp`  | Tests/examples for static libraries  | `bin\`           |


### In Detail

#### `app`
(no additional configuration changes)

#### `lib-dynamic`
* additional include directory `$(ProjectDir)..\include` (relative for usage as git module)
  + project file is assumed to be located within `src\`
* additional library directory for librarian
* post-build event: copying DLLs from `$(OutDir)` to `bin\` post-build

#### `lib-dynamic-app`
* additional include directory `$(ProjectDir)..\..\include` (relative for usage as git module)
  + project file is assumed to be located within `example\<example-name>\` or `test\<testname>\`

#### `lib-static`
* additional include directory `$(ProjectDir)..\include` (relative for usage as git module)
  + project file is assumed to be located within `src\`
* additional library directory for librarian

#### `lib-static-app`
* additional include directory `$(ProjectDir)..\..\include` (relative for usage as git module)
  + project file is assumed to be located within `example\<example-name>\` or `test\<testname>\`
