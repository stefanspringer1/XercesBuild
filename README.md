# XercesBuild: Binaries of XercesC++ with build instructions

Please see the [Xerces-C++ XML parser website](https://xerces.apache.org/xerces-c/) for code, licences, and documentation for Xerces-C++. This is just a simple repository containing:

- Some binaries of Xerces-C++. (The Xerces-C++ XML parser website provides no binaries.)
- The source code used.
- Some instructions for building. (Note that more build options are documented on [the Xerces-C++ website](hhttps://xerces.apache.org/xerces-c/build-3.html.).)

**The content of this repository comes without any warranty.** Usage of any parts is to your own risk.

Note that I am not affiliated to the Xerces-C++ project, nor am I attempting to somehow compete against the Xerces-C++ project website. The place to go if you want to know more about Xerces-C++ is [https://xerces.apache.org/xerces-c/](https://xerces.apache.org/xerces-c/). I am just using Xerces-C++, and this repository just contains some binaries that I have built for my own use and maybe some more specific instructions for building it on certain platforms. **If you do not want use those binaries here, just get the code from Xerces-C++ website and build the binary you need yourself.** Maybe some of my notes here then help.

The resources are in subdirectories named after the Xerces-C++ versions.

## Instructions for compiling Xerces-C++ on macOS and Linux on Intel

From inside the Xerces directory (not in src!):

```bash
./configure CFLAGS="-arch x86_64" CXXFLAGS="-arch x86_64"
cmake . -DCMAKE_BUILD_TYPE=Release
cmake --build . --config Release
```

## Instructions for compiling Xerces-C++ on Windows

Visual Studio should to be installed. The commands are then to be excuted from the "x64 Native Tools Command Prompt". Configure:

```bash
cmake -G "<Generator>" -A x64 . -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=<path to install directory>
```

For Visual Studio 2017:

```bash
cmake -G "Visual Studio 15 2017" -A x64 . -DCMAKE_BUILD_TYPE=Release
```

For Visual Studio 2017:

```bash
cmake -G "Visual Studio 16 2019" -A x64 . -DCMAKE_BUILD_TYPE=Release
```

Then build:

```bash
cmake --build . --config Release
```

You then find the DLL in `src\Release`.