cmake_minimum_required(VERSION 3.24)
project(apcc_libwebsockets C)

include(FetchContent)

# Build upstream directly: no vcpkg port or source patches are needed.
set(LWS_WITH_STATIC ON CACHE BOOL "" FORCE)
set(LWS_WITH_SHARED OFF CACHE BOOL "" FORCE)
set(LWS_WITHOUT_TESTAPPS ON CACHE BOOL "" FORCE)
set(LWS_WITH_EXPORT_LWSTARGETS OFF CACHE BOOL "" FORCE)
set(LWS_WITH_LIBUV OFF CACHE BOOL "" FORCE)
set(LWS_WITH_SSL ON CACHE BOOL "" FORCE)
set(LWS_WITH_SCHANNEL OFF CACHE BOOL "" FORCE)
set(LWS_WITH_HTTP3 OFF CACHE BOOL "" FORCE)
set(LWS_IPV6 ON CACHE BOOL "" FORCE)
set(LWS_WITHOUT_EXTENSIONS OFF CACHE BOOL "" FORCE)
set(LWS_WITH_ZLIB ON CACHE BOOL "" FORCE)
set(LWS_WITH_BUNDLED_ZLIB OFF CACHE BOOL "" FORCE)
set(DISABLE_WERROR ON CACHE BOOL "" FORCE)

# Includes upstream's compressed receive / decompression-draining fixes.
FetchContent_Declare(libwebsockets
    URL https://github.com/warmcat/libwebsockets/archive/baea18d8cd41239216ead77d9bcecd548114a660.tar.gz
    URL_HASH SHA512=dcd81ea0dbb54ade24352b5e6a70cf7e51bcf6eaffa3896efb750c40015ea7a1bc61a3c2c8cdb3582102ae0005b7ff271c30f45cb3bfc72a2bdd9ebcd0c68b7f
    DOWNLOAD_EXTRACT_TIMESTAMP TRUE
)
FetchContent_MakeAvailable(libwebsockets)
