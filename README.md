How to use the lib in your project:

1) Clone the vcpkg repo and install the required packages
   - git clone https://github.com/microsoft/vcpkg.git
   - cd vcpkg && bootstrap-vcpkg.bat
   - .\vcpkg.exe integrate install
   - .\vcpkg install jansson
   - .\vcpkg install libwebsockets
   - .\vcpkg install glib

2) Compile libwebsockets with extensions:
   -  edit .\vcpkg\ports\libwebsockets\portfile.cmake
   -  to cmake_configure options add the flag -DLWS_WITHOUT_EXTENSIONS=OFF

4) Create a visual studio project and add APCc.c + APCc.h

5) Add additional include directory ``$(_ZVcpkgCurrentInstalledDir)/include/glib-2.0;$(_ZVcpkgCurrentInstalledDir)/lib/glib-2.0/include;``


## License

APCc is a C port of [APCpp](https://github.com/N00byKing/APCpp), by N00byKing
and contributors. The C port and modifications are Copyright (c) 2024-2026
randomcodegen. The library is licensed under the GNU Lesser General Public
License version 2.1 (`LGPL-2.1-only`); see [LICENSE](LICENSE), reproduced from
APCpp. The upstream attribution and license are retained for the derived code.
License and source-file notices are restored on 2026-09-08.

This library is provided without warranty, including any implied warranty of
merchantability or fitness for a particular purpose. Jansson, GLib,
libwebsockets and their dependencies retain their own licenses.

When distributing binaries, include the required notices and provide the
corresponding modified library sources and build scripts. For statically
linked applications, also provide the application source and/or object files
and other materials needed to relink with modified libraries, following
LGPL 2.1 section 6. Recipients may modify the library and reverse engineer
the application to debug those modifications. Publish matching source and
relinking materials alongside each binary release.
