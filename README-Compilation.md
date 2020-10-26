## Compilation

Compiling with full features requires development files for several
external libraries. Below is a list of some important requirements.

全功能编译需要一些外部库的文件，以下是一些要求

The mpv build system uses [waf](https://waf.io/), but we don't store it in the
repository. The `./bootstrap.py` script will download the latest version
of waf that was tested with the build system.

build 系统用的是 waf, 但是我们不把 waf 存在这个代码库里

For a list of the available build options use `./waf configure --help`. If
you think you have support for some feature installed but configure fails to
detect it, the file `build/config.log` may contain information about the
reasons for the failure.

`./waf configure --help` 查看所有配置项
如果你觉得安装了开启某些功能的依赖，但是编译失败了，请看 `build/config.log` 文件里的信息

NOTE: To avoid cluttering the output with unreadable spam, `--help` only shows
one of the two switches for each option. If the option is autodetected by
default, the `--disable-***` switch is printed; if the option is disabled by
default, the `--enable-***` switch is printed. Either way, you can use
`--enable-***` or `--disable-**` regardless of what is printed by `--help`.

注意：为了让命令行输出尽可能干净，`--help` 命令指数出两个开关可能的其中一个选项。
如果一个选项是默认 autodeteced 的，那么输出 `--disable-***`
如果一个选项是默认关闭的，那么输出 `--enable-***`
总而言之 `--enable-***` 和 `--disable-**` 都能用

To build the software you can use `./waf build`: the result of the compilation
will be located in `build/mpv`. You can use `./waf install` to install mpv
to the *prefix* after it is compiled.

构建软件可以用 `./waf build` 命令
输出结果在 `build/mpv`

Example:

    ./bootstrap.py
    ./waf configure
    ./waf
    ./waf install

必须依赖（不完全列表）
Essential dependencies (incomplete list):

- gcc or clang
- X development headers (xlib, xrandr, xext, xscrnsaver, xinerama, libvdpau,
  libGL, GLX, EGL, xv, ...)
	这啥
- Audio output development headers (libasound/ALSA, pulseaudio)
- FFmpeg libraries (libavutil libavcodec libavformat libswscale libavfilter
  and either libswresample or libavresample)
	ffmpeg 的几个库
- zlib
- iconv (normally provided by the system libc)
- libass (OSD, OSC, text subtitles)
- Lua (optional, required for the OSC pseudo-GUI and youtube-dl integration)
- libjpeg (optional, used for screenshots only)
- uchardet (optional, for subtitle charset detection)
- nvdec and vaapi libraries for hardware decoding on Linux (optional)

Libass 的依赖
Libass dependencies (when building libass):

- gcc or clang, yasm on x86 and x86_64
- fribidi, freetype, fontconfig development headers (for libass)
- harfbuzz (optional, required for correct rendering of combining characters,
  particularly for correct rendering of non-English text on OSX, and
  Arabic/Indic scripts on any platform)

ffmpeg 的依赖
FFmpeg dependencies (when building FFmpeg):

- gcc or clang, yasm on x86 and x86_64
- OpenSSL or GnuTLS (have to be explicitly enabled when compiling FFmpeg)
- libx264/libmp3lame/libfdk-aac if you want to use encoding (have to be
  explicitly enabled when compiling FFmpeg)
- For native DASH playback, FFmpeg needs to be built with --enable-libxml2
  (although there are security implications, and DASH support has lots of bugs).
- AV1 decoding support requires dav1d.
- For good nvidia support on Linux, make sure nv-codec-headers is installed
  and can be found by configure.

Most of the above libraries are available in suitable versions on normal
Linux distributions. For ease of compiling the latest git master of everything,
you may wish to use the separately available build wrapper ([mpv-build][mpv-build])
which first compiles FFmpeg libraries and libass, and then compiles the player
statically linked against those.

[FAQ]: https://github.com/mpv-player/mpv/wiki/FAQ
[releases]: https://github.com/mpv-player/mpv/releases
[mpv-build]: https://github.com/mpv-player/mpv-build
[issue-tracker]:  https://github.com/mpv-player/mpv/issues
[release-policy]: https://github.com/mpv-player/mpv/blob/master/DOCS/release-policy.md
[windows_compilation]: https://github.com/mpv-player/mpv/blob/master/DOCS/compile-windows.md
[interface-changes]: https://github.com/mpv-player/mpv/blob/master/DOCS/interface-changes.rst
[api-changes]: https://github.com/mpv-player/mpv/blob/master/DOCS/client-api-changes.rst
[restore-old-bindings]: https://github.com/mpv-player/mpv/blob/master/etc/restore-old-bindings.conf
[contribute.md]: https://github.com/mpv-player/mpv/blob/master/DOCS/contribute.md
