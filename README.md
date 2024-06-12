mGBA Python Bindings
=====================

This is a fork of the Python bindings in the [mGBA repository](https://github.com/mgba-emu/mgba/tree/master/src/platform/python) and [libmgba-py repository](https://github.com/hanzi/libmgba-py)
with some modifications to get it to build easily on Raspberry Pi 3b or 4 (Pi 5 not tested).


## What this is (and isn't)

This provides Python bindings to libmgba, which is a library of
functions that mGBA uses internally.

Thus, you can use it to create a 'headless' emulator instance and
interact with its internal functions using Python.

It does **not** come with any GUI, i.e. you can't use it to just
remote control an instance of the mGBA emulator.


## Build Instructions on Raspberry OS Pi 64 bits (Bookworm)

### mGBA 0.10.1

   1. Install depedencies `sudo apt install git python3-setuptools python3-cffi python3-distutils python3-tk libmgba0.10 portaudio19-dev cmake libedit-dev libavcodec-dev libavfilter-dev libpng-dev libzip-dev libminizip-dev zipcmp zipmerge ziptool libepoxy-dev libelf-dev libsdl2-dev`
   2. `git clone https://github.com/hanzi/libmgba-py/`
   3. `git clone --depth 1 --branch 0.10.1 https://github.com/mgba-emu/mgba`
   4. `cp libmgba-py/core.* mgba/src/platform/python/`
   5. `cp libmgba-py/mgba/* mgba/src/platform/python/mgba/`
   6. `cd mgba/`
   7. `mkdir build`
   8. `cd build`
   9. `cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DBUILD_PYTHON=ON -DBUILD_QT=OFF ..`
   10. `make -j4` (this should take about 6 minutes on Pi4)
   
   the build files are located in `/home/pi/mgba/build/python/lib.linux-aarch64-cpython-312`
   
   You can clean libmgba and mgba folder if you want:
   1. `rm -rf /home/pi/libmgba-py/`
   2. `rm -rf /home/pi/mgba`

### mGBA 0.10.x

These instructions CAN ONLY WORK with the mGBA 0.10.x branches, replace x with the number desired

example for mGBA 0.10.3
   1. Install depedencies `sudo apt install git python3-setuptools python3-cffi python3-distutils python3-tk libmgba0.10 portaudio19-dev cmake libedit-dev libavcodec-dev libavfilter-dev libpng-dev libzip-dev libminizip-dev zipcmp zipmerge ziptool libepoxy-dev libelf-dev libsdl2-dev`
   2. `git clone https://github.com/hanzi/libmgba-py/`
   3. `git clone --depth 1 --branch 0.10.3 https://github.com/mgba-emu/mgba`
   4. `cp libmgba-py/core.* mgba/src/platform/python/`
   5. `cp libmgba-py/mgba/* mgba/src/platform/python/mgba/`
   6. `cd mgba/`
   7. `mkdir build`
   8. `cd build`
   9. `cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DBUILD_PYTHON=ON -DBUILD_QT=OFF ..`
   10. `make -j4` (this should take about 6 minutes on Pi4)

the build files are located in `/home/pi/mgba/build/python/lib.linux-aarch64-cpython-312`

   ### WARNING : DON'T DELETE NOR MOVE THE /home/pi/mgba/build FOLDER ! (unless you used mGBA 0.10.1 branch)

   but you can clean libmgba and mgba folder if you want:
   
   `rm -rf /home/pi/libmgba-py/`

## License

This code was taken from the offical mGBA repository and only modified
a bit, so [the original license terms](https://github.com/mgba-emu/mgba/#copyright)
apply:

> mGBA is Copyright © 2013 – 2023 Jeffrey Pfau.
> 
> It is distributed under the Mozilla Public License version 2.0.  
> A copy of the license is available in the distributed LICENSE file.
