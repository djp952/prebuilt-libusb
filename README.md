# LIBUSB 1.0.23   
[https://github.com/libusb/libusb](https://github.com/libusb/libusb)   
  
**TARGETS**   
* linux-i686 (gcc-4.9)   
* linux-x86_64 (gcc-4.9)   
* linux-armel (gcc-4.9)   
* linux-armhf (gcc-4.9)   
* linux-aarch64 (gcc-4.9)   
* raspbian-armhf   
* osx-x86_64 (apple-darwin15)   
   
**BUILD ENVIRONMENT**  
* Windows 10 x64 1909 (18363) "November 2019 Update"   
* Windows Subsystem for Linux   
* [Ubuntu on Windows 16.04 LTS](https://www.microsoft.com/store/productId/9PJN388HP8C9)   
* OSXCROSS Cross-Compiler (with Mac OSX 10.11 SDK)   
  
**CONFIGURE UBUNTU ON WINDOWS**   
Open "Ubuntu"   
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install gcc-4.9 g++-4.9 libc6-dev:i386 libstdc++-4.9-dev:i386 lib32gcc-4.9-dev 
sudo apt-get install gcc-4.9-arm-linux-gnueabihf g++-4.9-arm-linux-gnueabihf gcc-4.9-arm-linux-gnueabi g++-4.9-arm-linux-gnueabi gcc-4.9-aarch64-linux-gnu g++-4.9-aarch64-linux-gnu
sudo apt-get install autoconf libtool make p7zip-full python
```
   
**CONFIGURE OSXCROSS CROSS-COMPILER**   
* Generate the MAC OSX 10.11 SDK Package for OSXCROSS by following the instructions provided at [PACKAGING THE SDK](https://github.com/tpoechtrager/osxcross#packaging-the-sdk).  The suggested version of Xcode to use when generating the SDK package is Xcode 7.3.1 (May 3, 2016).
* Open "Ubuntu"   
```
sudo apt-get install cmake clang llvm-dev libxml2-dev uuid-dev libssl-dev libbz2-dev zlib1g-dev
git clone https://github.com/tpoechtrager/osxcross --depth=1
cp {MacOSX10.11.sdk.tar.bz2} osxcross/tarballs/
UNATTENDED=1 osxcross/build.sh
```
   
**BUILD LIBUSB (linux-i686)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
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
Get libusb/.libs/libusb-1.0.a from lib/.libs   

**BUILD LIBUSB (linux-x86_64)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
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
Get libusb/.libs/libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (linux-armel)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
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
Get libusb/.libs/libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (linux-armhf)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
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
Get libusb/.libs/libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (linux-aarch64)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
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
Get libusb/.libs/libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (raspbian-armhf)**   
Open "Ubuntu"   
```
git clone https://github.com/raspberrypi/tools.git raspberrypi --depth=1
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
export PATH=$(pwd)/raspberrypi/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin:$PATH
export CC=arm-linux-gnueabihf-gcc
export AR=arm-linux-gnueabihf-gcc-ar
export RANLIB=arm-linux-gnueabihf-gcc-ranlib
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=arm-linux-gnueabihf --with-pic --disable-udev
make
```
Get libusb.h from libusb   
Get libusb/.libs/libusb-1.0.a from lib/.libs   
   
**BUILD LIBUSB (osx-x86_64)**   
Open "Ubuntu"   
```
git clone https://github.com/libusb/libusb -b v1.0.23 --depth=1
export PATH=$(pwd)/osxcross/target/bin:$PATH
export CC=x86_64-apple-darwin15-clang
export AR=x86_64-apple-darwin15-ar
export RANLIB=x86_64-apple-darwin15-ranlib
export CFLAGS="-mmacosx-version-min=10.9 -stdlib=libc++"
export LIBS=-ldl
cd libusb
./bootstrap.sh
./configure --host=x86_64-apple-darwin15 --with-pic --disable-udev
OSXCROSS_NO_EXTENSION_WARNINGS=1 make
```
Get libusb.h from libusb   
Get libusb/.libs/libusb-1.0.a from lib/.libs   
   
## ADDITIONAL LICENSE INFORMATION
   
**XCODE AND APPLE SDKS AGREEMENT**   
The instructions provided above indirectly reference the use of intellectual material that is the property of Apple, Inc.  This intellectual material is not FOSS (Free and Open Source Software) and by using it you agree to be bound by the terms and conditions set forth by Apple, Inc. in the [Xcode and Apple SDKs Agreement](https://www.apple.com/legal/sla/docs/xcode.pdf).
