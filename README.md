Compile:

1) Clone the vcpkg repo and install the required packages
- git clone https://github.com/microsoft/vcpkg.git
- cd vcpkg && bootstrap-vcpkg.bat
- .\vcpkg.exe integrate install
- .\vcpkg install jansson
- .\vcpkg install libwebsockets
- .\vcpkg install glib

2) Create a visual studio project and add APCc.c + APCc.h

3) Add additional include directory $(_ZVcpkgCurrentInstalledDir)/include/glib-2.0;$(_ZVcpkgCurrentInstalledDir)/lib/glib-2.0/include;
