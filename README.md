# XercesBuild: Binaries of XercesC++ with build instructions

Please see the [Xerces-C++ XML parser website](https://xerces.apache.org/xerces-c/) for code, licences, and documentation for Xerces-C++. This is just a simple repository containing:

- Some binaries (dynamic libraries) of Xerces-C++. (The Xerces-C++ XML parser website provides no binaries.)
- The source code used.
- Some instructions for building. (Note that more build options are documented on [the Xerces-C++ website](hhttps://xerces.apache.org/xerces-c/build-3.html.).)

Note that I am not affiliated to the Xerces-C++ project, nor am I attempting to somehow compete against the Xerces-C++ project website. The place to go if you want to know more about Xerces-C++ is [https://xerces.apache.org/xerces-c/](https://xerces.apache.org/xerces-c/). I am just using Xerces-C++, and this repository just contains some binaries that I have built for my own use and maybe some more specific instructions for building it on certain platforms. **If you do not want use those binaries here, just get the code from Xerces-C++ website and build the binary you need yourself.** Maybe some of my notes here then help.

The resources are in subdirectories named after the Xerces-C++ versions.

## Instructions for compiling Xerces-C++ on macOS and Linux on Intel

You need to have a compiler suite installed. E.g. on macOS, install Xcode plus the Command Line Tools for Xcode (which should automatically be installed the when you open Xcode the first time). You also need to have `cmake` installed, e.g. on macOS via [Homebrew](https://brew.sh).

From inside the Xerces directory (not in src!):

```bash
./configure
cmake . -DCMAKE_BUILD_TYPE=Release
cmake --build . --config Release
```

You can explicitly choose an architecture (not on Red Hat 7):

```bash
./configure CFLAGS="-arch x86_64" CXXFLAGS="-arch x86_64"
```

You then find the library as `src/libxerces-c-3.2.*`.

Get the info about the architecture for a library on macOS:

```bash
lipo -info libxerces-c-3.2.dylib
```

Examples for outputs from this command:

- `Non-fat file: libxerces-c-3.2.dylib is architecture: arm64`
- `Non-fat file: libxerces-c-3.2.dylib is architecture: x86_64`

## Instructions for compiling Xerces-C++ on Windows

Visual Studio should to be installed. The commands are then to be excuted from the "x64 Native Tools Command Prompt". Configure:

```bash
cmake -G "<Generator>" -A x64 . -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=<path to install directory>
```

For Visual Studio 2017:

```bash
cmake -G "Visual Studio 15 2017" -A x64 . -DCMAKE_BUILD_TYPE=Release
```

For Visual Studio 2019:

```bash
cmake -G "Visual Studio 16 2019" -A x64 . -DCMAKE_BUILD_TYPE=Release
```

Then build:

```bash
cmake --build . --config Release
```

You then find the DLL in `src\Release`.

---

Legal notice: Usage of any of the included material is to your own risk. The Xerces-C++ source is from [https://xerces.apache.org/xerces-c/](https://xerces.apache.org/xerces-c/) and is used under the Apache 2 license.