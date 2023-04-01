# Compile instruction

## Before compiling

please check the [Releases](https://github.com/Franklalalala/usenauty/releases). There are pre-compiled linux and windows versions, respectively.

## Compile a linux version

The [CXX standard](https://en.wikipedia.org/wiki/C%2B%2B17) is set to be **17**, which means the gcc version need to be 8 or higher. Additionally, the cmake version needs to be **3.1** or higher.

With these conditions, one can follow these steps:

1. Load gcc and cmake modules. For example:

```
module load compiler/gcc/8.4.0
module load compiler/cmake/3.15.6
```

2. Make sure the compiler works.

```
which gcc
# /public/software/compiler/gnu/gcc-8.4.0/bin/gcc # The gcc path
export  CC=/public/software/compiler/gnu/gcc-8.4.0/bin/gcc
export  CXX=/public/software/compiler/gnu/gcc-8.4.0/bin/g++
```

3. Compile with commands as following:

```
git clone https://github.com/Franklalalala/usenauty
cd usenauty
mkdir build
cd build
cmake .. -G "Unix Makefiles"
make
```

## Compile a Window version

The easiest way to compile is setup a [Visual Studio 2017](https://en.wikipedia.org/wiki/Microsoft_Visual_Studio#2017) toolset and drag the whole project into the IDE.

VS17 will automatically compile the project.

Otherwise, one needs to prepare a compiler and cmake that meets requirements. See above.

The compile line is the same as above.

# File Comments

## File differences with source library codes

Changed some files from [source](https://pallini.di.uniroma1.it/index.html) Version 2.7R1 (MAY 19 2019):

- naututil.h:
  For msvc use, change `<sys/time.h>` to `"times.h"` and `times.c` with Macro defined for arch choice.
- gtools.h:
  For msvc use, change `<sys/wait.h>` to `"wait.h"`
- showg.c:
  Add a compiler choice `ASLIB`

# Code structure and function enhancement information

- New `CMakeLists.txt` instead of `makefile`.
- All `boolean` type code are changed to `_Boolean`
- Change a Macro in `nauty.h`:
  `FIRSTBITNZ(x)` to `msc_bsr_xx(x)` where call `unsigned long p` instead of `unsigned long *p`

File and `wait.h` is from `https://github.com/win32ports`, By MIT License. Some necessary changed is with them.
File `times.h` is used for necessary function and types.

Additionally, this project conducted several changes comparing to the original modification in [saltball/usenauty (github.com)](https://github.com/saltball/usenauty). 

* The step and random mode are created on top of the base mode.
* Code structures are refactored to enable some suitable API.
* Bugs fixed for compilation in the Linux platform. (credit to @saltball)

# Other info
This repo is try to use `nauty` for some chemical research and create some new API. It's still on going.
Original License is [COPYRIGHT](libnauty/COPYRIGHT)
