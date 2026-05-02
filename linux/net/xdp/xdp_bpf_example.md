# Build
下载 bpf-example:
地址: https://github.com/xdp-project/bpf-examples

命令:
```
git clone --depth=1 https://github.com/xdp-project/bpf-examples.git
cd bpf-examples/    
```

安装依赖: `sudo apt install libmnl-dev linux-tools-5.15.0-130-generic linux-tools-generic`
可能需要: `sudo apt install libc6-dev-i386`

编译:
```
ERROR: Need clang version >= 11, found 10 (10.0.0-4ubuntu1 )
make: *** [Makefile:53: config.mk] Error 1
```

clang版本太低, 安装clang-18:
```
wget https://apt.llvm.org/llvm.sh
sudo bash llvm.sh 18
sudo mv /usr/bin/clang /usr/bin/clang-old
sudo ln /usr/bin/clang-18 /usr/bin/clang
```
PS: 参考资料: https://ubuntuhandbook.org/index.php/2023/09/how-to-install-clang-17-or-16-in-ubuntu-22-04-20-04/

编译:
```
$ make
sh configure
clang: 18.1.8 (11~20.04.2)
libmnl support: yes
libbpf support: submodule
ELF support: yes
zlib support: yes
libxdp support: submodule
Configuring libxdp to use our libbpf submodule
configure: 209: ./configure: Permission denied

lib

  libbpf
    CC       install/lib/libbpf.a
    INSTALL  install/lib/libbpf.a

  libxdp
    CC       install/lib/libxdp.a
Submodule 'libbpf' (https://github.com/libbpf/libbpf.git) registered for path 'lib/libbpf'
Cloning into '/home/lixiang/download/bpf-examples/lib/xdp-tools/lib/libbpf'...
llc: error: invalid target 'bpf'.
make[4]: *** [Makefile:138: xdp-dispatcher.o] Error 1
make[3]: *** [Makefile:20: libxdp] Error 2
make[2]: *** [Makefile:28: libxdp] Error 2
make[1]: *** [Makefile:68: install/lib/libxdp.a] Error 2
make: *** [Makefile:35: lib] Error 2
```

修改 `~/.bashrc`, 增加:
```
export PATH=/usr/lib/llvm-18/bin/:$PATH
```

然后:`source ~/.bashrc`, 继续编译:
```
$ make
... ...
AF_XDP-example
    CC       xdpsock
xdpsock.c:27:10: fatal error: sys/capability.h: No such file or directory
   27 | #include <sys/capability.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make[1]: *** [../lib/common.mk:83: xdpsock] Error 1
make: *** [Makefile:38: AF_XDP-example] Error 2
```

安装库: `sudo apt-get install libcap-dev`

继续:
```
$ make
... ...
AF_XDP-example
    CC       xdpsock
xdpsock.c: In function ‘main’:
xdpsock.c:2003:16: warning: unused variable ‘r’ [-Wunused-variable]
 2003 |  struct rlimit r = {RLIM_INFINITY, RLIM_INFINITY};
      |                ^
At top level:
xdpsock.c:653:13: warning: ‘swap_mac_addresses’ defined but not used [-Wunused-function]
  653 | static void swap_mac_addresses(void *data)
      |             ^~~~~~~~~~~~~~~~~~
    CLANG    xdpsock_kern.o
    LLC      xdpsock_kern.o

xdp-synproxy
    CLANG    xdp_synproxy_kern.o
xdp_synproxy_kern.c:27:9: warning: 'tcp_flag_word' macro redefined [-Wmacro-redefined]
   27 | #define tcp_flag_word(tp) (((union tcp_word_hdr *)(tp))->words[3])
      |         ^
/usr/include/linux/tcp.h:70:9: note: previous definition is here
   70 | #define tcp_flag_word(tp) ( ((union tcp_word_hdr *)(tp))->words [3]) 
      |         ^
1 warning generated.
    LLC      xdp_synproxy_kern.o
    GEN      xdp_synproxy_kern.skel.h
    CC       xdp_synproxy
```

