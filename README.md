Overview
--------
This script downloads and compiles tcpdump for use on Android devices.

It creates PIE (Position Independant Executable) files, so they also work on Lollipop and Marshmallow.

How to use
----------
Install the latest [Android NDK](http://developer.android.com/ndk/downloads/index.html) then:

    export NDK=/path/to/ndk
    ./build-android-tcpdump

Options
-------
The script allows to download the latest stable version or the latest version from the GIT repository.
Also it's capable of creating tcpdump for multiple architectures.

    ./build-android-tcpdump -h
    Usage: build-android-tcpdump [OPTIONS]
    Version: 1.0
    Automatically download and build tcpdump for Android devices
    Also valid for Lollipop and Marshmallow

    OPTIONS:
    -h              Show this help
    -a=ARCHS        Space separated architectures to build or all. Default: all
                    Valid architectures: arm arm64 mips mips64 x86 x86_64
    -n=NDK_PATH     Path of the Android NDK root
                    Default: Value of the NDK environment variable
    -b=BUILD_DIR    Destination of the compiled tcpdump. Default: build
    -s              Don't strip the final executable
    -j=NPROCS       Number of simultaneous jobs when compiling
                    Default: Number of cores of the machine
    -t=TCPDUMP_VER  Version of tcpdump or "master" for the latest revision in the repository
                    Default: 4.7.4
    -l=LIBPCAP_VER  Version of libpcap or "master" for the latest revision in the repository
                    Default: 1.7.4
    -u=TCPDUMP_DIR  Don't download tcpdump. Use the one in the specified directory
    -m=LIBPCAP_DIR  Don't download libpcap. Use the one in the specified directory

Notes
-----
The latest current stable libpcap version 1.7.4 doesn't compile for architectures using Android platforms < 21 (arm, mips and x86). For the moment, as a workaround you can use the GIT version for libpcap:

    ./build-android-tcpdump -l master
