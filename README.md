# rust-pi
POC for building a rust binary cross compiled for raspberry Pi

## Macos M1 silicon build
```bash
brew tap messense/macos-cross-toolchains
brew install armv7-unknown-linux-gnueabihf 
```

```bash
TARGET=armv7-unknown-linux-gnueabihf                                       
export TARGET_CC=$TARGET-gcc
export TARGET_AR=$TARGET-ar
export CC_armv7_unknown_linux_gnu=$TARGET-gcc
export CXX_armv7_unknown_linux_gnu=$TARGET-g++
export AR_armv7_unknown_linux_gnu=$TARGET-ar
export CARGO_TARGET_ARMV7_UNKNOWN_LINUX_GNUEABIHF_LINKER=$TARGET-gcc
export CMAKE_TOOLCHAIN_FILE_armv7_unknown_linux_gnueabihf=$(pwd)/armv7.cmake
cargo build --release --target $TARGET
```
Now `scp` the binary to the Pi and run it!

## Github Actions Build
See the `.github/workflows/cross-compile.yml` file for the build steps. The build is triggered on every push to the `main` branch.
