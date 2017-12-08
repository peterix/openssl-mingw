# openssl-mingw
Windows OpenSSL builds for MultiMC, because things that depend on Visual Studio can take a hike.

## Build process

1. Get 32bit MSYS2 from here: [msys2.org](http://www.msys2.org/)
2. Install it.
3. Run the MSYS2 shell.
4. Install the basic build packages:
   ```
   pacman -S base-devel mingw-w64-i686-toolchain tar gzip wget git
   ```
   Just let it install everything it suggests. It's fine.
5. Clone this repo:
   Example:
   ```
   git clone https://github.com/peterix/openssl-mingw.git
   cd openssl-mingw
   ```
6. Configure and build it:
   ```
   cd source
   ./Configure --prefix=$PWD/../dist no-idea no-mdc2 no-rc5 shared mingw
   make depend && make && make install_sw
   ```
7. And that's how you build OpenSSL that works with the pre-built Qt 5.6.3 in 2017. Results are in the `dist` folder that's next to the `source` folder.

See [releases](https://github.com/peterix/openssl-mingw/releases/) for prebuilt DLLs you can just drop in and use.