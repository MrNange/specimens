GCC、g++编译时出现出现这样的问题
/usr/local/lib/liblua.a(loadlib.o)：在函数‘ll_loadfunc’中：
loadlib.c:(.text+0x928)：对‘dlsym’未定义的引用
loadlib.c:(.text+0x979)：对‘dlerror’未定义的引用
loadlib.c:(.text+0x9a8)：对‘dlopen’未定义的引用
loadlib.c:(.text+0xa3b)：对‘dlerror’未定义的引用
/usr/local/lib/liblua.a(loadlib.o)：在函数‘gctm’中：
loadlib.c:(.text+0xd18)：对‘dlclose’未定义的引用

编译时要在尾部加上 -lm -llua -ldl解决了：
gcc -o test test.c -llua -lm -ldl

编译代码，生成动态链接库时：
  gcc mylib.c -fPIC -shared -o mylib.so
