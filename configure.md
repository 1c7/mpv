例子

```bash
➜  1c7_mpv git:(master) ✗ ./waf configure --enable-libmpv-shared                
Setting top to                           : /Users/remote_edit/Desktop/用所选项目新建的文件夹 2/1c7_mpv 
Setting out to                           : /Users/remote_edit/Desktop/用所选项目新建的文件夹 2/1c7_mpv/build 
# 这个 top 和 out 要看看定义在哪里了
Checking for waf version in 1.8.4-2.1.0  : ok 
# 检查范围版本
Checking for program 'cc'                : /usr/bin/cc 
Checking for program 'pkg-config'        : /usr/local/bin/pkg-config 
Checking for program 'ar'                : /usr/bin/ar 
Checking for program 'rst2html'          : /usr/local/bin/rst2html.py 
Checking for program 'rst2man'           : /usr/local/bin/rst2man.py 
Checking for program 'rst2pdf'           : not found 
Checking for program 'windres'           : not found 
Checking for program 'perl'              : /usr/bin/perl 
Checking for 'clang' (C compiler)        : /usr/bin/cc 
# 检查 target OS
Detected target OS:                      : os-darwin 
Checking for macOS SDK                   : /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.15.sdk (version found: 10.15.6) 
Checking for swift (Swift compiler)      : /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/swift 
Checking for dynamic Swift Library       : /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/lib/swift/macosx 
Checking for static Swift Library        : not found 
# 这一堆 compiler flag 是干嘛的
Checking for compiler flags -std=c11     : yes 
Checking for compiler flags -Werror -Werror=implicit-function-declaration : yes 
Checking for compiler flags -Werror -Wno-error=deprecated-declarations    : yes 
Checking for compiler flags -Werror -Wno-error=unused-function            : yes 
Checking for compiler flags -Werror -Wempty-body                          : yes 
Checking for compiler flags -Werror -Wdisabled-optimization               : yes 
Checking for compiler flags -Werror -Wstrict-prototypes                   : yes 
Checking for compiler flags -Werror -Wno-format-zero-length               : yes 
Checking for compiler flags -Werror -Werror=format-security               : yes 
Checking for compiler flags -Werror -Wno-redundant-decls                  : yes 
Checking for compiler flags -Werror -Wvla                                 : yes 
Checking for compiler flags -Werror -Wno-format-truncation                : no 
Checking for compiler flags -Werror -Wimplicit-fallthrough                : yes 
Checking for compiler flags -Werror -fno-math-errno                       : yes 
Checking for LGPL (version 2.1 or later) build                            : disabled 
Checking for GPL (version 2 or later) build                               : yes 
# 启用 cli player
Checking for mpv CLI player                                               : yes 
Checking for shared library                                               : yes 
Checking for static library                                               : disabled 
# 看看开启 static library 会输出啥
Checking for static build                                                 : disabled
# 这个也一样试试
Checking for whether to include binary compile time                       : yes 
# ?
Checking for whether to optimize                                          : yes 
Checking for whether to compile-in debugging information                  : yes 
Checking for unit tests (development only)                                : disabled 
Checking for enable ta leak report by default (development only)          : disabled 
Checking for manpage generation                                           : yes 
Checking for html manual generation                                       : disabled 
# 输出 html 手册
Checking for pdf manual generation                                        : disabled 
# 输出 pdf 手册
Checking for dynamic loader                                               : yes 
Checking for C plugins                                                    : yes 
Checking for inline assembly (currently without effect)                   : yes 
Checking for generate a clang compilation database                        : disabled 
Checking for static Swift linking                                         : disabled 
Checking for compiler support for noexecstack                             : no 
Checking for linker support for --nxcompat --no-seh --dynamicbase         : no 
Checking for -lm                                                          : yes 
Checking for MinGW                                                        : os-win32 not found 
Checking for POSIX environment                                            : yes 
Checking for Android environment                                          : no 
Checking for tvOS environment                                             : no 
Checking for Android EGL support                                          : android not found 
Checking for development environment                                      : yes 
Checking for macOS Swift build tools                                      : yes (version found: 5.3) 
Checking for Universal Windows Platform                                   : disabled 
Checking for win32 desktop APIs                                           : os-win32 not found 
Checking for internal pthread wrapper for win32 (Vista+)                  : posix found 
Checking for POSIX threads                                                : yes 
Checking for pthread runtime debugging wrappers                           : disabled 
Checking for C11 stdatomic.h                                              : yes 
Checking for linking with -lrt                                            : no 
Checking for iconv                                                        : yes 
Checking for w32/dos paths                                                : os-win32 not found 
Checking for glob() POSIX support                                         : yes 
Checking for glob() win32 replacement                                     : posix found 
Checking for any glob() support                                           : yes 
Checking for vt.h                                                         : no 
Checking for consio.h                                                     : no 
Checking for gbm.h                                                        : no 
Checking for GLIBC API for setting thread name                            : no 
Checking for OSX API for setting thread name                              : yes 
Checking for BSD API for setting thread name                              : osx-thread-name found 
Checking for BSD's fstatfs()                                              : yes 
Checking for Linux's fstatfs()                                            : os-linux not found 
Checking for Lua                                                          : yes (version found: luajit) 
Checking for Javascript (MuJS backend)                                    : yes 
Checking for SSA/ASS support                                              : yes 
# 字幕支持
Checking for zlib                                                         : yes 
Checking for Bluray support                                               : yes 
Checking for dvdnav support                                               : disabled 
Checking for cdda support (libcdio)                                       : disabled 
Checking for uchardet support                                             : yes 
Checking for librubberband support                                        : yes 
Checking for libzimg support (high quality software scaler)               : yes 
Checking for LCMS2 support                                                : yes 
Checking for VapourSynth filter bridge                                    : yes 
Checking for libarchive wrapper for reading zip files and more            : no ('libarchive >= 3.4.0' not found) 
Checking for DVB input module                                             : disabled 
Checking for SDL2                                                         : disabled 
# SDL2
Checking for SDL2 gamepad input                                           : sdl2 not found 
Checking for FFmpeg library                                               : yes 
Checking for libavdevice                                                  : yes 
Checking for Disable all known FFmpeg ABI violations                      : disabled 
Checking for SDL2 audio output                                            : sdl2 not found 
Checking for PulseAudio audio output                                      : no ('libpulse >= 1.0' not found) 
Checking for JACK audio output                                            : no ('jack' not found) 
Checking for OpenAL audio output                                          : disabled 
Checking for OpenSL ES audio output                                       : no 
Checking for ALSA audio output                                            : no ('alsa >= 1.0.18' not found) 
Checking for CoreAudio audio output                                       : yes 
Checking for AudioUnit output for iOS                                     : no 
Checking for WASAPI audio output                                          : os-win32 not found 
Checking for SDL2 video output                                            : sdl2 not found 
Checking for Cocoa                                                        : yes 
Checking for DRM                                                          : vt.h not found 
Checking for GBM                                                          : gbm.h not found 
Checking for wayland-scanner                                              : no 
Checking for wayland-protocols                                            : no ('wayland-protocols >= 1.15' not found) 
Checking for Wayland                                                      : wayland-protocols not found 
Checking for Linux memfd_create()                                       : wayland not found 
Checking for X11                                                          : no ('x11 >= 1.0.0 xscrnsaver >= 1.0.0 xext >= 1.0.0 xinerama >= 1.0.0 xrandr >= 1.2.0' not found) 
Checking for Xv video output                                              : x11 not found 
Checking for OpenGL Cocoa Backend                                         : yes 
# OpenGL Cocoa Backend   
Checking for OpenGL X11/GLX (deprecated/legacy)                           : disabled 
Checking for Raspberry Pi support                                         : disabled 
Checking for EGL 1.4                                                      : no ('egl' not found) 
Checking for OpenGL X11 EGL Backend                                       : x11 not found 
Checking for OpenGL DRM EGL Backend                                       : drm not found 
Checking for OpenGL Wayland Backend                                       : wayland not found 
Checking for OpenGL Win32 Backend                                         : win32-desktop not found 
Checking for OpenGL/DirectX Interop Backend                               : gl-win32 not found 
Checking for OpenGL ANGLE headers                                         : os-win32 not found 
Checking for OpenGL Win32 ANGLE Library                                   : egl-angle not found 
Checking for OpenGL Win32 ANGLE Backend                                   : egl-angle not found 
Checking for VDPAU acceleration                                           : x11 not found 
Checking for VDPAU with OpenGL/X11                                        : vdpau not found 
Checking for VAAPI acceleration                                           : x11 not found 
Checking for VAAPI (X11 support)                                          : vaapi not found 
Checking for VAAPI (Wayland support)                                      : vaapi not found 
Checking for VAAPI (DRM/EGL support)                                      : vaapi not found 
Checking for VAAPI EGL on X11                                             : vaapi-x11 not found 
Checking for VAAPI EGL                                                    : vaapi-x-egl not found 
Checking for CACA                                                         : no ('caca >= 0.99.beta18' not found) 
Checking for JPEG support                                                 : yes 
Checking for Direct3D support                                             : win32-desktop not found 
Checking for libshaderc SPIR-V compiler (shared library)                  : no 
Checking for libshaderc SPIR-V compiler (static library)                  : no 
Checking for libshaderc SPIR-V compiler                                   : shaderc-shared not found 
Checking for SPIRV-Cross SPIR-V shader converter (shared library)         : no ('spirv-cross-c-shared' not found) 
Checking for SPIRV-Cross SPIR-V shader converter (static library)         : no ('spirv-cross' not found) 
Checking for SPIRV-Cross SPIR-V shader converter                          : spirv-cross-shared not found 
Checking for Direct3D 11 video output                                     : win32-desktop not found 
Checking for iOS OpenGL ES hardware decoding interop support              : no 
Checking for OpenGL without platform-specific code (e.g. for libmpv)      : yes 
Checking for OpenGL context support                                       : yes 
Checking for libplacebo support                                           : no ('libplacebo >= 1.18.0' not found) 
Checking for Vulkan context support                                       : libplacebo not found 
Checking for VAAPI Vulkan                                                 : vaapi not found 
Checking for EGL helper functions                                         : egl not found 
Checking for libavcodec videotoolbox hwaccel                              : yes 
Checking for Videotoolbox with OpenGL                                     : yes 
Checking for D3D11VA hwaccel                                              : os-win32 not found 
Checking for DXVA2 hwaccel                                                : d3d-hwaccel not found 
Checking for OpenGL/DirectX Interop Backend DXVA2 interop                 : gl-dxinterop not found 
Checking for CUDA Headers and dynamic loader                              : no ('ffnvcodec >= 8.2.15.7' not found) 
Checking for CUDA acceleration                                            : ffnvcodec not found 
Checking for CUDA with graphics interop                                   : cuda-hwaccel not found 
Checking for Raspberry Pi MMAL hwaccel                                    : rpi not found 
Checking for w32 executable                                               : os-win32 not found 
Checking for macOS Touch Bar support                                      : yes 
Checking for macOS 10.11 SDK Features                                     : yes 
Checking for macOS 10.12.2 SDK Features                                   : yes 
Checking for macOS 10.14 SDK Features                                     : yes 
Checking for macOS Media Player support                                   : yes 
Checking for macOS libmpv backend                                         : yes 
Adding conditional Swift flags:                                           : yes 
Writing configuration header:                                             : config.h 
# 最后的输出结果是这个 config.h 文件？
'configure' finished successfully (9.091s)
➜  1c7_mpv git:(master) ✗ 
```