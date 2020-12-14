# LIBUSB 1.0.24   
[https://github.com/libusb/libusb](https://github.com/libusb/libusb)   
  
**TARGETS**   
* linux-i686 (gcc-4.9)   
* linux-x86_64 (gcc-4.9)   
* linux-armel (gcc-4.9)   
* linux-armhf (gcc-4.9)   
* linux-aarch64 (gcc-4.9)   
* android-21-armeabi-v7a (ndk-r20b/api-21)   
* android-21-arm64-v8a (ndk-r20b/api-21)   
* android-21-x86 (ndk-r20b/api-21)   
* android-28-armeabi-v7a (ndk-r20b/api-28)   
* android-28-arm64-v8a (ndk-r20b/api-28)   
* android-28-x86 (ndk-r20b/api-28)   
   
**BUILD ENVIRONMENT**  
* Windows 10 x64 1909 (18363) "November 2019 Update"   
* Windows Subsystem for Linux   
* [Ubuntu on Windows 16.04 LTS](https://www.microsoft.com/store/productId/9PJN388HP8C9)   
  
**CONFIGURE UBUNTU ON WINDOWS**   
Open "Ubuntu"   
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install gcc-4.9 g++-4.9 libc6-dev:i386 libstdc++-4.9-dev:i386 lib32gcc-4.9-dev 
sudo apt-get install gcc-4.9-arm-linux-gnueabihf g++-4.9-arm-linux-gnueabihf gcc-4.9-arm-linux-gnueabi g++-4.9-arm-linux-gnueabi gcc-4.9-aarch64-linux-gnu g++-4.9-aarch64-linux-gnu
sudo apt-get install autoconf libtool make p7zip-full python
```
   
**CONFIGURE ANDROID TOOLCHAINS**   
Open "Ubuntu"   
```
wget https://dl.google.com/android/repository/android-ndk-r20b-linux-x86_64.zip
7z x android-ndk-r20b-linux-x86_64.zip
```
  
**BUILD LIBUSB (linux-i686)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export CC=gcc-4.9
export AR=gcc-ar-4.9
export RANLIB=gcc-ranlib-4.9
export CFLAGS="-m32 -I/usr/include/i386-linux-gnu"
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host i686-pc-linux-gnu --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   

**BUILD LIBUSB (linux-x86_64)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export CC=gcc-4.9
export AR=gcc-ar-4.9
export RANLIB=gcc-ranlib-4.9
export CFLAGS="-I/usr/include/x86_64-linux-gnu"
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (linux-armel)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export CC=arm-linux-gnueabi-gcc-4.9
export AR=arm-linux-gnueabi-gcc-ar-4.9
export RANLIB=arm-linux-gnueabi-gcc-ranlib-4.9
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=arm-linux-gnueabi --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (linux-armhf)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export CC=arm-linux-gnueabihf-gcc-4.9
export AR=arm-linux-gnueabihf-gcc-ar-4.9
export RANLIB=arm-linux-gnueabihf-gcc-ranlib-4.9
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=arm-linux-gnueabihf --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (linux-aarch64)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export CC=aarch64-linux-gnu-gcc-4.9
export AR=aarch64-linux-gnu-gcc-ar-4.9
export RANLIB=aarch64-linux-gnu-gcc-ranlib-4.9
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=aarch64-linux-gnu --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBCURL (android-21-armeabi-v7a)**
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/arm-linux-androideabi-ar
export AS=$TOOLCHAIN/bin/arm-linux-androideabi-as
export CC=$TOOLCHAIN/bin/armv7a-linux-androideabi21-clang
export CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi21-clang++
export LD=$TOOLCHAIN/bin/arm-linux-androideabi-ld
export RANLIB=$TOOLCHAIN/bin/arm-linux-androideabi-ranlib
export STRIP=$TOOLCHAIN/bin/arm-linux-androideabi-strip
export CPPFLAGS="-I$(pwd)/prebuilt-libz/android-21-armeabi-v7a/include"
export LDFLAGS="-L$(pwd)/prebuilt-libz/android-21-armeabi-v7a/lib" 
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=arm-linux-androideabi --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBCURL (android-21-arm64-v8a)**
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/aarch64-linux-android-ar
export AS=$TOOLCHAIN/bin/aarch64-linux-android-as
export CC=$TOOLCHAIN/bin/aarch64-linux-android21-clang
export CXX=$TOOLCHAIN/bin/aarch64-linux-android21-clang++
export LD=$TOOLCHAIN/bin/aarch64-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/aarch64-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/aarch64-linux-android-strip
export CPPFLAGS="-I$(pwd)/prebuilt-libz/android-21-arm64-v8a/include"
export LDFLAGS="-L$(pwd)/prebuilt-libz/android-21-arm64-v8a/lib" 
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=aarch64-linux-android --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBCURL (android-21-x86)**
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/i686-linux-android-ar
export AS=$TOOLCHAIN/bin/i686-linux-android-as
export CC=$TOOLCHAIN/bin/i686-linux-android21-clang
export CXX=$TOOLCHAIN/bin/i686-linux-android21-clang++
export LD=$TOOLCHAIN/bin/i686-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/i686-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/i686-linux-android-strip
export CPPFLAGS="-I$(pwd)/prebuilt-libz/android-21-x86/include"
export LDFLAGS="-L$(pwd)/prebuilt-libz/android-21-x86/lib" 
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=i686-linux-android --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBCURL (android-28-armeabi-v7a)**
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/arm-linux-androideabi-ar
export AS=$TOOLCHAIN/bin/arm-linux-androideabi-as
export CC=$TOOLCHAIN/bin/armv7a-linux-androideabi28-clang
export CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi28-clang++
export LD=$TOOLCHAIN/bin/arm-linux-androideabi-ld
export RANLIB=$TOOLCHAIN/bin/arm-linux-androideabi-ranlib
export STRIP=$TOOLCHAIN/bin/arm-linux-androideabi-strip
export CPPFLAGS="-I$(pwd)/prebuilt-libz/android-28-armeabi-v7a/include"
export LDFLAGS="-L$(pwd)/prebuilt-libz/android-28-armeabi-v7a/lib" 
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=arm-linux-androideabi --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBCURL (android-28-arm64-v8a)**
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/aarch64-linux-android-ar
export AS=$TOOLCHAIN/bin/aarch64-linux-android-as
export CC=$TOOLCHAIN/bin/aarch64-linux-android28-clang
export CXX=$TOOLCHAIN/bin/aarch64-linux-android28-clang++
export LD=$TOOLCHAIN/bin/aarch64-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/aarch64-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/aarch64-linux-android-strip
export CPPFLAGS="-I$(pwd)/prebuilt-libz/android-28-arm64-v8a/include"
export LDFLAGS="-L$(pwd)/prebuilt-libz/android-28-arm64-v8a/lib" 
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=aarch64-linux-android --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
**BUILD LIBCURL (android-28-x86)**
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.24 --depth=1
export TOOLCHAIN=$(pwd)/android-ndk-r20b/toolchains/llvm/prebuilt/linux-x86_64
export AR=$TOOLCHAIN/bin/i686-linux-android-ar
export AS=$TOOLCHAIN/bin/i686-linux-android-as
export CC=$TOOLCHAIN/bin/i686-linux-android28-clang
export CXX=$TOOLCHAIN/bin/i686-linux-android28-clang++
export LD=$TOOLCHAIN/bin/i686-linux-android-ld
export RANLIB=$TOOLCHAIN/bin/i686-linux-android-ranlib
export STRIP=$TOOLCHAIN/bin/i686-linux-android-strip
export CPPFLAGS="-I$(pwd)/prebuilt-libz/android-28-x86/include"
export LDFLAGS="-L$(pwd)/prebuilt-libz/android-28-x86/lib" 
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=i686-linux-android --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb-1.0.a from lib/.libs   
   
