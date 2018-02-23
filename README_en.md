To avoid setting the environment variable "LD_LIBRARY_PATH" every time Python is launched, option "-rpath" should be configed when building the source code.

for exemple:
./configure --enable-shared --prefix=/opt/python \
            LDFLAGS=-Wl,-rpath=/opt/python-2.7.14/lib

(PYTHON_CONFIGURE_OPTS='--enable-shared'，this option is not needed) 

Rules and orders for linker(ld-linux) to search dynamic libs:
1. Path indicated by "DT_RPATH" in ELF files
   You can config "DT_RPATH" by adding options "-Wl,rpath" behind gcc
   
2. Paths indicated by environment variable "LD_LIBRARY_PATH"

3. Paths saved in file "/etc/ld.so.cache"
   Execute command "ldconfig" by root after the file "/etc/ld.so.cache" is modified
   
4. The default lib path: /lib

5. The default lib path: /usr/lib

