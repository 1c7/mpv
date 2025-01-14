## 第三方依赖写到哪里去了？

## 如何编译出  macOS 下的 dylib？因为 IINA 有这些东西
```
./waf configure
./waf configure --enable-libmpv-shared --enable-static-build --enable-html-build --disable-manpage-build
```
configure 命令跑完之后，输出的东西是 `build/config.h`
`build/` 目录里除了这个文件还有另外几个文件  

--enable-libmpv-static 会报错，看看咋回事
--enable-pdf-build 也会报错

## waf
```
./waf --help
```

waf [commands] [options]

Main commands (example: ./waf build -j4)
  build    : executes the build
  clean    : cleans the project
  configure: configures the project
  dist     : makes a tarball for redistributing the sources
  distcheck: checks if the project compiles (tarball from 'dist')
  distclean: removes build folders and data
  install  : installs the targets on the system
  list     : lists the targets to execute
  step     : executes tasks in a step-by-step fashion, for debugging
  uninstall: removes the targets installed

Options:
  --version             show program's version number and exit
  -c COLORS, --color=COLORS
                        whether to use colors (yes/no/auto) [default: auto]
  -j JOBS, --jobs=JOBS  amount of parallel jobs (8)
  -k, --keep            continue despite errors (-kk to try harder)
  -v, --verbose         verbosity level -v -vv or -vvv [default: 0]
  --zones=ZONES         debugging zones (task_gen, deps, tasks, etc)
  -h, --help            show this help message and exit

  Configuration options:
    -o OUT, --out=OUT   build dir for the project
    -t TOP, --top=TOP   src dir for the project
    --check-c-compiler=CHECK_C_COMPILER
                        list of C compilers to try [clang gcc]

  Build and installation options:
    -p, --progress      -p: progress bar; -pp: ide output
    --targets=TARGETS   task generators, e.g. "target1,target2"
    --variant=VARIANT   variant name for saving configuration and build results
    --enable-lgpl       enable LGPL (version 2.1 or later) build [disable]
    --disable-cplayer   disable mpv CLI player [enable]
    --enable-libmpv-shared
                        enable shared library [disable]
    --enable-libmpv-static
                        enable static library [disable]
    --enable-static-build
                        enable static build [disable]
    --disable-build-date
                        disable whether to include binary compile time [enable]
    --disable-optimize  disable whether to optimize [enable]
    --disable-debug-build
                        disable whether to compile-in debugging information [enable]
    --enable-tests      enable unit tests (development only) [disable]
    --enable-ta-leak-report
                        enable enable ta leak report by default (development only) [disable]
    --disable-manpage-build
                        disable manpage generation [autodetect]
    --enable-html-build
                        enable html manual generation [disable]
    --enable-pdf-build  enable pdf manual generation [disable]
    --disable-cplugins  disable C plugins [autodetect]
    --disable-asm       disable inline assembly (currently without effect) [enable]
    --enable-clang-database
                        enable generate a clang compilation database [disable]
    --enable-swift-static
                        enable static Swift linking [disable]

  Step options:
    --files=FILES       files to process, by regexp, e.g. "*/main.c,*/test/main.o"

  Installation and uninstallation options:
    -f, --force         force file installation
    --distcheck-args=ARGS
                        arguments to pass to distcheck

  Installation prefix:
    By default, "waf install" will put the files in "/usr/local/bin", "/usr/local/lib" etc. An installation prefix other than
    "/usr/local" can be given using "--prefix", for example "--prefix=$HOME"

    --prefix=PREFIX     installation prefix [default: '/usr/local/']
    --destdir=DESTDIR   installation root [default: '']
    --exec-prefix=EXEC_PREFIX
                        installation prefix for binaries [PREFIX]

  Installation directories:
    --bindir=BINDIR     user commands [EXEC_PREFIX/bin]
    --sysconfdir=SYSCONFDIR
                        host-specific configuration [PREFIX/etc]
    --libdir=LIBDIR     object code libraries [EXEC_PREFIX/lib]
    --includedir=INCLUDEDIR
                        header files [PREFIX/include]
    --datarootdir=DATAROOTDIR
                        architecture-independent data root [PREFIX/share]
    --datadir=DATADIR   architecture-independent data [DATAROOTDIR]
    --mandir=MANDIR     manual pages [DATAROOTDIR/man]
    --docdir=DOCDIR     documentation root [DATAROOTDIR/doc/PACKAGE]
    --htmldir=HTMLDIR   HTML documentation [DOCDIR]
    --confdir=CONFDIR   directory for installing configuration files [SYSCONFDIR/mpv]
    --zshdir=ZSHDIR     directory for installing zsh completion functions [DATADIR/zsh/site-functions]
    --confloaddir=CONFLOADDIR
                        directory for installing configuration files load directory [CONFDIR]
    --bashdir=BASHDIR   directory for installing bash completion functions [DATADIR/bash-completion/completions]

  optional features:
    --disable-android   disable Android environment [autodetect]
    --disable-tvos      disable tvOS environment [autodetect]
    --disable-egl-android
                        disable Android EGL support [autodetect]
    --disable-swift     disable macOS Swift build tools [autodetect]
    --enable-uwp        enable Universal Windows Platform [disable]
    --disable-win32-internal-pthreads
                        disable internal pthread wrapper for win32 (Vista+) [autodetect]
    --enable-pthread-debug
                        enable pthread runtime debugging wrappers [disable]
    --disable-stdatomic
                        disable C11 stdatomic.h [autodetect]
    --disable-iconv     disable iconv [autodetect]
    --disable-lua       disable Lua [autodetect]
    --disable-javascript
                        disable Javascript (MuJS backend) [autodetect]
    --disable-zlib      disable zlib [autodetect]
    --disable-libbluray
                        disable Bluray support [autodetect]
    --enable-dvdnav     enable dvdnav support [disable]
    --enable-cdda       enable cdda support (libcdio) [disable]
    --disable-uchardet  disable uchardet support [autodetect]
    --disable-rubberband
                        disable librubberband support [autodetect]
    --disable-zimg      disable libzimg support (high quality software scaler) [autodetect]
    --disable-lcms2     disable LCMS2 support [autodetect]
    --disable-vapoursynth
                        disable VapourSynth filter bridge [autodetect]
    --disable-libarchive
                        disable libarchive wrapper for reading zip files and more [autodetect]
    --enable-dvbin      enable DVB input module [disable]
    --enable-sdl2       enable SDL2 [disable]
    --disable-sdl2-gamepad
                        disable SDL2 gamepad input [autodetect]
    --disable-libavdevice
                        disable libavdevice [autodetect]
    --enable-ffmpeg-strict-abi
                        enable Disable all known FFmpeg ABI violations [disable]
    --lua=LUA_VER       select Lua package which should be autodetected. Choices: 51 51deb 51obsd 51fbsd 52 52deb 52arch 52fbsd luajit
    --swift-flags=SWIFT_FLAGS
                        Optional Swift compiler flags

  audio outputs:
    --disable-sdl2-audio
                        disable SDL2 audio output [autodetect]
    --disable-pulse     disable PulseAudio audio output [autodetect]
    --disable-jack      disable JACK audio output [autodetect]
    --enable-openal     enable OpenAL audio output [disable]
    --disable-opensles  disable OpenSL ES audio output [autodetect]
    --disable-alsa      disable ALSA audio output [autodetect]
    --disable-coreaudio
                        disable CoreAudio audio output [autodetect]
    --disable-audiounit
                        disable AudioUnit output for iOS [autodetect]
    --disable-wasapi    disable WASAPI audio output [autodetect]

  video outputs:
    --disable-sdl2-video
                        disable SDL2 video output [autodetect]
    --disable-cocoa     disable Cocoa [autodetect]
    --disable-drm       disable DRM [autodetect]
    --disable-gbm       disable GBM [autodetect]
    --disable-wayland-scanner
                        disable wayland-scanner [autodetect]
    --disable-wayland-protocols
                        disable wayland-protocols [autodetect]
    --disable-wayland   disable Wayland [autodetect]
    --disable-x11       disable X11 [autodetect]
    --disable-xv        disable Xv video output [autodetect]
    --disable-gl-cocoa  disable OpenGL Cocoa Backend [autodetect]
    --enable-gl-x11     enable OpenGL X11/GLX (deprecated/legacy) [disable]
    --enable-rpi        enable Raspberry Pi support [disable]
    --disable-egl       disable EGL 1.4 [autodetect]
    --disable-egl-x11   disable OpenGL X11 EGL Backend [autodetect]
    --disable-egl-drm   disable OpenGL DRM EGL Backend [autodetect]
    --disable-gl-wayland
                        disable OpenGL Wayland Backend [autodetect]
    --disable-gl-win32  disable OpenGL Win32 Backend [autodetect]
    --disable-gl-dxinterop
                        disable OpenGL/DirectX Interop Backend [autodetect]
    --disable-egl-angle
                        disable OpenGL ANGLE headers [autodetect]
    --disable-egl-angle-lib
                        disable OpenGL Win32 ANGLE Library [autodetect]
    --disable-egl-angle-win32
                        disable OpenGL Win32 ANGLE Backend [autodetect]
    --disable-vdpau     disable VDPAU acceleration [autodetect]
    --disable-vdpau-gl-x11
                        disable VDPAU with OpenGL/X11 [autodetect]
    --disable-vaapi     disable VAAPI acceleration [autodetect]
    --disable-vaapi-x11
                        disable VAAPI (X11 support) [autodetect]
    --disable-vaapi-wayland
                        disable VAAPI (Wayland support) [autodetect]
    --disable-vaapi-drm
                        disable VAAPI (DRM/EGL support) [autodetect]
    --disable-vaapi-x-egl
                        disable VAAPI EGL on X11 [autodetect]
    --disable-caca      disable CACA [autodetect]
    --disable-jpeg      disable JPEG support [autodetect]
    --disable-direct3d  disable Direct3D support [autodetect]
    --disable-shaderc   disable libshaderc SPIR-V compiler [autodetect]
    --disable-spirv-cross
                        disable SPIRV-Cross SPIR-V shader converter [autodetect]
    --disable-d3d11     disable Direct3D 11 video output [autodetect]
    --disable-ios-gl    disable iOS OpenGL ES hardware decoding interop support [autodetect]
    --disable-plain-gl  disable OpenGL without platform-specific code (e.g. for libmpv) [autodetect]
    --disable-gl        disable OpenGL context support [autodetect]
    --disable-libplacebo
                        disable libplacebo support [autodetect]
    --disable-vulkan    disable Vulkan context support [autodetect]

  hwaccels:
    --disable-videotoolbox-gl
                        disable Videotoolbox with OpenGL [autodetect]
    --disable-d3d-hwaccel
                        disable D3D11VA hwaccel [autodetect]
    --disable-d3d9-hwaccel
                        disable DXVA2 hwaccel [autodetect]
    --disable-gl-dxinterop-d3d9
                        disable OpenGL/DirectX Interop Backend DXVA2 interop [autodetect]
    --disable-cuda-hwaccel
                        disable CUDA acceleration [autodetect]
    --disable-cuda-interop
                        disable CUDA with graphics interop [autodetect]
    --disable-rpi-mmal  disable Raspberry Pi MMAL hwaccel [autodetect]

  standalone app:
    --disable-macos-touchbar
                        disable macOS Touch Bar support [autodetect]
    --disable-macos-10-11-features
                        disable macOS 10.11 SDK Features [autodetect]
    --disable-macos-10-12-2-features
                        disable macOS 10.12.2 SDK Features [autodetect]
    --disable-macos-10-14-features
                        disable macOS 10.14 SDK Features [autodetect]
    --disable-macos-media-player
                        disable macOS Media Player support [autodetect]
    --disable-macos-cocoa-cb
                        disable macOS libmpv backend [autodetect]