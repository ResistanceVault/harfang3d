<img src="https://github.com/harfang3d/image-storage/raw/main/brand/logo_harfang3d_owl_only.png" align="right" width="200"/>

# HARFANG® 3D engine

[![PyPI](https://img.shields.io/pypi/v/harfang)](https://pypi.org/project/harfang)
[![Downloads](https://pepy.tech/badge/harfang)](https://pepy.tech/project/harfang)
[![Downloads](https://pepy.tech/badge/harfang/month)](https://pepy.tech/project/harfang)

HARFANG®3D is an all-in-one 3D visualization library usable in C++, Python, Lua and Go.
#### Table of contents

1. [About](#section_1)
    - [Features](#subsection_1a)
    - [Screenshots](#subsection_1b)
2. [Download](#section_2)
3. [Building the SDK](#section_3)
    - [Prerequisites](#subsection_3a)
    - [Building](#subsection_3b)
4. [Using the C++ SDK](#section_4)
5. [Version](#section_5)
6. [License](#section_6)
7. [Contribute](#section_7)
8. [Support Harfang](#section_8)

<a name="section_1"></a>
# About

HARFANG®3D is an easy-to-adapt, cross-platform, multi-language, powerful and optimized solution to integrate with embedded systems, into existing environments and combining features to meet the industrial standards of real-time 3D imaging.

The HARFANG®3D architecture makes it easy to meet the requirements for hardware integration, display performance and security.

HARFANG®3D is written in C++ and is based on the open-source bgfx library supporting Vulkan, Metal, DirectX (from 9 to 12), OpenGL and OpenGL ES. It Builds on Windows, Linux, Intel and ARM.

<a name="subsection_1a"></a>
## Features

Platforms supported
* Win32 and Win64 Intel
* Linux 64 Intel
* Aarch 64 ARM

Scene API
* Node & component based
* Performance oriented

Rendering pipeline
* Low-spec PBR rendering pipeline
* High-spec 'AAA' rendering pipeline (screen space GI & reflection)
* Support of user pipeline shaders

VR API
* VR support via OpenVR/SteamVR with Eye tracking
* Compatible with the HTC Vive/Vive Pro, Valve Index, Lenovo Explorer, Oculus Rift S

Physics API
* Rigid bodies, collisions, mechanical constraints, ray casting

Audio API
* Play/stream WAV/OGG formats
* 3D audio spatialization

Languages supported
* C++
* Python _(3.2+)_
* Lua _(5.4)_
* Go _(1+, experimental)_
<a name="subsection_1b"></a>
## Screenshots

The following screenshots were captured on a 1080GTX in 1080P running at 60FPS.

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/2.0.111/sun_temple_aaa.png)

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/2.0.111/sun_temple_aaa_2.png)

*(Sun Temple, courtesy of the Open Research Content Archive (ORCA))*

<a name="section_2"></a>
# Download

You can download the HARFANG binaries from the official website:
https://dev.harfang3d.com/releases

<a name="section_3"></a>
# Build the SDK

<a name="subsection_3a"></a>
## Prerequisites

* Git
* CMake 3.19+
* CPython 3.2+
* Go 1+ _(for Harfang Go module)_
* Doxygen _(for Harfang C++ SDK documentation)_
* Autodesk FBX SDK _(for FBX Converter)_

### Windows
* Visual Studio 2019 _(C++ compiler and IDE)_
* MinGW _(for Harfang Go module)_

### Linux
* GCC 9 or above
* CLang 

<a name="subsection_3b"></a>
## Building

1. Clone the `Harfang 3D` repository including its submodules.
    ```
    git clone --recursive -j8 https://github.com/harfang3d/harfang3d.git
    cd harfang3d
    ```

1. Create build directory. Note that the described directory layout is not mandatory.
    ```
    mkdir build
    cd build
    ``` 

1. Clone Fabgen.
    ```
    git clone https://github.com/ejulien/FABGen.git
    ```

1. Download and install Autodesk FBX SDK.

1. Create a directory that will hold the build system generated by CMake.
    ```
    mkdir cmake
    cd cmake
    ```

1. Generate the build system using CMake. For example, on Windows it will be:
    ```
    cmake ../.. -G "Visual Studio 16 2019" -A x64 \
        -DCMAKE_INSTALL_PREFIX:PATH="D:/harfang/build/install" \
        -DPYTHON_EXECUTABLE:FILEPATH="C:/Python36/python.exe" \
        -DHG_FABGEN_PATH:PATH="D:/harfang/build/fabgen" \
        -DHG_FBX_SDK:PATH="D:/fbx_sdk" 
    ``` 

    * `CMAKE_INSTALL_PREFIX` specifies the directory where the Harfang SDK will installed.
    * `PYTHON_EXECUTABLE` is the path the Python 3 interpreter.
    * `FABGEN_PATH` is the path to Fabgen binding generator.
    * `HG_FBX_SDK` is the path to Autodesk FBX SDK.

    &nbsp;    
    Here is the list of available CMake options.

    * __C++ SDK__
        * `HG_BUILD_CPP_SDK` : Build C++ SDK (default: __OFF__).
        * `HG_BUILD_TESTS`   : Build C++ SDK unit tests (default: __OFF__).
        * `HG_BUILD_DOCS`    : Build API and C++ SDK documentations (default: __OFF__).
        * `HG_ENABLE_BULLET3_SCENE_PHYSICS` : Enable Bullet physics API (default: __ON__).
        * `HG_ENABLE_RECAST_DETOUR_API` : Enable Recast/Detour navigation mesh and path finding API (default: __ON__).
        * `HG_ENABLE_OPENVR_API`   : Enable OpenVR API (default: __OFF__).
        * `HG_ENABLE_SRANIPAL_API` : Enable VIVE Eye and Facial Tracking SDK (SRanipal) API (default: __OFF__).
    * __Tools__
        * `HG_BUILD_ASSETC`             : Build AssetC asset compiler (default: __ON__).
        * `HG_BUILD_ASSIMP_CONVERTER`   : Build Assimp based 3D model converter (default: __ON__).
        * `HG_BUILD_FBX_CONVERTER`      : Build FBX converter (default: __ON__).
        * `HG_BUILD_GLTF_IMPORTER`      : Build GLTF importer (default: __ON__).
        * `HG_BUILD_GLTF_EXPORTER`      : Build GLTF exporter (default: __ON__).
    * __Bindings__
        * `HG_BUILD_HG_LUA`     : Build Harfang LUA module (default: __OFF__).
        * `HG_BUILD_HG_PYTHON`  : Build Harfang Python module (wheel) (default: __OFF__).
        * `HG_BUILD_HG_GO`      : Build Harfang GO module (default: __OFF__).
        
    &nbsp;    

1. Build the SDK.
    ```
    cmake --build . --config Release --target INSTALL
    ```
    _Note: On Linux you will need to explicitly specify the build type with `-DCMAKE_BUILD_TYPE=Release`_  

    Depending on the set of option passed to CMake the install directory will contain the following subdirectories:
    * `cppsdk` : Harfang C++ SDK.
    * `hg_python` : Harfang Python module.
    * `hg_lua` : Harfang LUA module.
    * `hg_go` : Harfang Go module.
    * `assetc` : Asset compiler.
    * `assimp_converter` : Assimp 3D model converter.
    * `fbx_converter` : FBX converter.
    * `gltf_importer` : GLTF importer.
    * `gltf_exporter` : GLTF exporter.
    
### Notes on Visual Studio Code

1. Install the CMakeTools extension.

1. Copy the `harfang/.vscode/template_settings.json` file to `harfang/.vscode/settings.json` and edit it to reflect your local installation.

1. Open the `harfang` folder in Visual Studio Code. CMakeTools should succesfully configure the project.

<a name="section_4"></a>
# Use the SDK

The Harfang C++ SDK directory `cppsdk` contains the following:
* `bin` : depending on the configuration used, this directory contains either a `Release` or `Debug` subdirectory with all the shared libraries.
* `lib` : like the `bin` directory, it contains a subdirectories named after the configuration used during build (`Release` or `Debug`) with all the generated static libraries.
* `include` : contains all the C++ include files of Harfang public API.
* `cmake` : contains the CMake configuration files. 

To add the Harfang C++ SDK to your CMake project, just add the following to the `CMakeLists.txt` file:
```cmake
find_package(harfang REQUIRED
    COMPONENTS cppsdk
    PATHS ${HG_CPPSDK_PATH}
    NO_DEFAULT_PATH
)
```
with `HG_CPPSDK_PATH` the path to the `cppsdk` directory. For example, if we follow the directory layout given above, it will be `D:/harfang/build/install/cppsdk`.

Targets should link against the following libraries.
* `hg::engine` 
* `hg::foundation` 
* `hg::platform`
* `hg::libluadll`

The `install_cppsdk_dependencies` function installs the Harfang C++ SDK shared libraries dependencies.
```cmake
install_cppsdk_dependencies(destination component)
```
* `destination` : is the library where the shared libraries will be installed.
* `component` : installation component name.

<a name="section_5"></a>
# Version

Harfang follows the Semantic Versioning Specification (SemVer) (http://semver.org).

Given a version number MAJOR.MINOR.PATCH, increment the:

* MAJOR version when you make incompatible API changes,
* MINOR version when you add functionality in a backwards-compatible manner, and
* PATCH version when you make backwards-compatible bug fixes.

<a name="section_6"></a>
# License

Harfang is licensed under the GPLv3, LGPLv3 and a commercial license:<br>
https://www.harfang3d.com/license

<a name="section_7"></a>
# Contribute
## Contributor License Agreement

By contributing your code to HARFANG you grant the [HARFANG3D organization](https://www.harfang3d.com/en_US/legal) a non-exclusive, irrevocable, worldwide, royalty-free, sublicenseable, transferable license under all of Your relevant intellectual property rights (including copyright, patent, and any other rights), to use, copy, prepare derivative works of, distribute and publicly perform and display the Contributions on any licensing terms, including without limitation:
(a) open source licenses like the MIT license; and (b) binary, proprietary, or commercial licenses. Except for the licenses granted herein, You reserve all right, title, and interest in and to the Contribution.

You confirm that you are able to grant us these rights. You represent that You are legally entitled to grant the above license. If Your employer has rights to intellectual property that You create, You represent that You have received permission to make the Contributions on behalf of that employer, or that Your employer has waived such rights for the Contributions.

You represent that the Contributions are Your original works of authorship, and to Your knowledge, no other person claims, or has the right to claim, any right in any invention or patent related to the Contributions. You also represent that You are not legally obligated, whether by entering into an agreement or otherwise, in any way that conflicts with the terms of this license.

The [HARFANG3D organization](https://www.harfang3d.com/en_US/legal) acknowledges that, except as explicitly described in this Agreement, any Contribution which you provide is on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OR CONDITIONS OF TITLE, NON-INFRINGEMENT, MERCHANTABILITY, OR FITNESS FOR A PARTICULAR PURPOSE.

<a name="section_8"></a>
# How to support Harfang?

There are numerous ways to help Harfang grow its community:

* Give the repository a [Star :star:](https://github.com/harfang3d/harfang3d)
* Purchase a license of [Harfang Studio](https://www.harfang3d.com/en_US/studio)
* Subscribe to Harfang [Youtube channel](https://www.youtube.com/c/HARFANG3D/videos)
* Follow us on [Twitter](https://twitter.com/harfang3dengine/)
* Leave a Comment/Like on [Alternative To](https://alternativeto.net/software/harfang-3d/about/)

<a name="section_9"></a>
# More screenshots...

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/3.1.1/sun_temple_aaa.png)

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/3.1.1/sun_temple_aaa_2.png)

*(Sun Temple, courtesy of the Open Research Content Archive (ORCA))*

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/3.1.1/cafe_exterior_aaa.png)

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/3.1.1/cafe_exterior_aaa_2.png)

*(Bistro, courtesy of the Open Research Content Archive (ORCA))*

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/3.1.1/sponza_atrium_aaa.png)

![alt text](https://raw.githubusercontent.com/harfang3d/image-storage/main/portfolio/3.1.1/sponza_atrium_aaa_2.png)

*(Sponza Atrium GLTF, courtesy of Crytek/Themaister)*

