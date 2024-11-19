# Onion Link to Main Repo
https://vub63vv26q6v27xzv2dtcd25xumubshogm67yrpaz2rculqxs7jlfqad.onion.pet/torzu-emu/torzu  (remove .pet to access onion directly)

# Method I: MSVC Build for Windows (MS Visual Studio)

### MSVC: Overview

  * Install Minimal Dependencies (details and setup below)
      * Visual Studio Community 2022
      * CMake
      * Vulkan SDK
      * Python
      * Git for Windows
  * Build via Command Line (simplest if dependencies are installed correctly)
  * (or) Build with GUI Tools (backup graphical interface)


### MSVC: Install Minimal Dependencies

To build torzu on Windows with Visual Studio, you need to install:

  * **[Visual Studio 2022 Community](https://visualstudio.microsoft.com/downloads/)**
    * **Update to the latest version if already installed. (continued below)**

  ![](https://i.imgur.com/0jwV1hW.png)

  * **Visual Studio 2022 Community (continued)**
    * Be sure to select "Desktop development with C++"
    * Select the MSVC components outlined in red below (**especially VS 2019 build tools**.)

  ![](https://i.imgur.com/NtSnqjm.png)

  ![](https://i.imgur.com/YLr1Qw2.png)

  * **[CMake](https://cmake.org/download/)** - Used to generate Visual Studio project files. Choose 32-bit or 64-bit according to your system. 
    * **If it asks to be added to your system PATH, say YES.**

  ![](https://i.imgur.com/7pteS6d.png)

  * **[Vulkan SDK](https://vulkan.lunarg.com/sdk/home#windows)** - Make sure to select Latest SDK. 
    * **If it asks to be added to your system PATH, say YES.**

  ![](https://i.imgur.com/aHCJxsR.png)
  
  * **[Python](https://www.python.org/downloads/windows/)** - Select latest stable Windows installer. Choose 32-bit or 64-bit according to your system. 
    * **If it asks to be added to your system PATH, say YES.**

  ![](https://i.imgur.com/xIEuM6R.png)

  * **[Git for Windows](https://gitforwindows.org)** - (see next step)

  ![](https://i.imgur.com/UeSzkBw.png)

  * When installing Git, include it in your system PATH by choosing the "**Git from the command line and also from 3rd-party software**" option. 

  ![](https://i.imgur.com/x0rRs1t.png)

  * **REBOOT YOUR SYSTEM, to be sure all dependencies are registered before proceeding.**

---
---

## MSVC: Build from the Command Line

* Open a command line (cmd.exe), navigate to a directory where you want to download the repo, then pick one option to clone into a subdirectory named "torzu":

**from Notabug repo:**
```
git clone --depth 1 https://notabug.org/litucks/torzu.git
```
**from Torzu repo (assuming Tor is installed as a service, download tor browser and run tor.exe):**
```
git -c http.proxy=socks5h://127.0.0.1:9050 clone --depth 1 http://vub63vv26q6v27xzv2dtcd25xumubshogm67yrpaz2rculqxs7jlfqad.onion/torzu-emu/torzu.git
```

* Assuming all dependencies were installed correctly, you should be able to continue from the above `git clone` and run the following commands to build:

```
cd torzu
git submodule update --init --recursive
mkdir build
cd build
cmake .. -G "Visual Studio 17 2022" -A x64 -DYUZU_TESTS=OFF
cmake --build . --config Release
```
* You'll find the resulting files in the `build/bin/Release` folder. To make it a portable install with all AppData files local to the torzu folder, add a "user" folder:
```
cd bin
cd Release
mkdir user
```

* **ERRORS:** If you get an error after running the first cmake command (such as a missing library or CMakeLists.txt), first try running `git submodule update --init --recursive` from inside "torzu" folder again. If that doesn't work, try deleting the whole "torzu" folder and recloning via git from the beginning (as sometimes submodules will be incomplete without throwing an error.)

---
---


