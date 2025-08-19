# 准备
for docker
```
# apt-get install -y locales
# locale-gen en_US.UTF-8
# update-locale LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8
```

安装依赖
```
sudo apt-get install build-essential chrpath cpio debianutils diffstat file gawk gcc git iputils-ping libacl1 liblz4-tool locales python3 python3-git python3-jinja2 python3-pexpect python3-pip python3-subunit socat texinfo unzip wget xz-utils zstd
```
参考：https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html#build-host-packages

拉取代码：
```
mkdir riscv-yocto && cd riscv-yocto
repo init -u https://github.com/riscv/meta-riscv  -b master -m tools/manifests/riscv-yocto.xml
repo sync
repo start work --all
```

build
```
MACHINE=qemuriscv64 bitbake core-image-full-cmdline
```

run
```
MACHINE=qemuriscv64 runqemu core-image-full-cmdline nographic slirp snapshot
```

run(for Debug)
```
MACHINE=qemuriscv64 runqemu core-image-full-cmdline nographic slirp snapshot qemuparams="-s -S"
```

gdb attach
```
riscv64-linux-gnu-gdb build/tmp/work/qemuriscv64-poky-linux/linux-yocto/6.12.41+git/linux-qemuriscv64-standard-build/vmlinux
... ...
(gdb) set substitute-path /usr/src/kernel/ /home/yang.li09/github/riscv-yocto/build/tmp/work-shared/qemuriscv64/kernel-source/
(gdb) directory /home/yang.li09/github/riscv-yocto/build/tmp/work-shared/qemuriscv64/kernel-source/
(gdb) target remote :1234
(gdb) b kmalloc_noprof
(gdb) continue
Continuing.
[Switching to Thread 1.3]

Thread 3 hit Breakpoint 1, start_kernel () at /usr/src/kernel/init/main.c:905
905             char *command_line;
```

generate kernel compile_commands:
```
cd /home/yang.li09/github/riscv-yocto/build/tmp/work-shared/qemuriscv64/kernel-source
python3 scripts/clang-tools/gen_compile_commands.py -d /home/yang.li09/github/riscv-yocto/build/tmp/work/qemuriscv64-poky-linux/linux-yocto/6.12.41+git/linux-qemuriscv64-standard-build/

ls -l compile_commands.json
-rw-rw-r-- 1 yang.li09 yang.li09 11886342 Aug 19 09:58 compile_commands.json
```
