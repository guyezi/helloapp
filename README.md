Let's start!
---
1. First, install Ubuntu 64bit (Ubuntu 18 LTS x86 is recommended).

2. Run `sudo apt-get update` in the terminal, and then run
    `
    sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync
    `

3. Run `git clone https://github.com/guyezi/helloapp` or `git clone -b branch https://github.com/guyezi/helloapp` to clone the source, and then `cd lede` to enter the directory

```bash
wget --no-check-certificate https://mirrors.cloud.tencent.com/lede/releases/21.02.0-rc1/targets/x86/64/openwrt-sdk-21.02.0-rc1-x86-64_gcc-8.4.0_musl.Linux-x86_64.tar.xz
xz -d openwrt-sdk-21.02.0-rc1-x86-64_gcc-8.4.0_musl.Linux-x86_64.tar.xz
tar -xvf openwrt-sdk-21.02.0-rc1-x86-64_gcc-8.4.0_musl.Linux-x86_64.tar
cd openwrt-sdk-21.02.0-rc1-x86-64_gcc-8.4.0_musl.Linux-x86_64
git clone https://github.com/guyezi/helloapp package/helloapp
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig
```

4. ```bash
   ./scripts/feeds update -a
   ./scripts/feeds install -a
   make menuconfig
   ```

5. ```make -j8 download V=99```

6. ```$ make package/obm-mmp/clean V=99```

8. ```$ make package/obm-mmp/compile V=99```

9. ```$ make package/obm-mmp/install V=99```
 
10. ```$ make package/obm-mmp/{clean,compile,install} V=99```
 
11. ```$ make package/feeds/packages/nginx/{clean, compile, install} V=99```
 
12. ```$ make tools/automake/compile```

13. ```$ make toolchain/{clean, compile, install}```

重编kernel:

14. ```$ make target/linux/compile```

15. ```$ make target/linux/install```

16. ```$ make target/linux/{clean, compile, install}```


