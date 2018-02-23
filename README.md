# config-rpath-for-python



为避免每次启动Python时都必须使用 LD_LIBRARY_PATH 指定运行时库路径,您可以使用 -rpath 链接器选项在构建时指定它:

./configure --enable-shared --prefix=/opt/python \

            LDFLAGS=-Wl,-rpath=/opt/python-2.7.14/lib

(PYTHON_CONFIGURE_OPTS='--enable-shared'，  ) 

动态链接器(ld.so或ld-linux.so.x),按照下面的顺序来搜索需要的动态库

1. ELF可执行文件中动态段中DT_RPATH所指定的路径，编译代码时，可以对gcc加入链接参数"-Wl,rpath"指定动态库搜索路径

2. 环境变量 LD_LIBRARY_PATH 指定的路径

3. /etc/ld.so.cache 中所缓存的动态路径，可以通过修改/etc/ld.so.conf指定，修改后使用ldconfig生效

4. 默认的动态库搜索路径 /lib

5. 默认的 /usr/lib
