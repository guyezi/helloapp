Let's start!
---
1. First, install Ubuntu 64bit (Ubuntu 20.04 LTS x64).

2. Run `sudo apt-get update` in the terminal, and then run

```bash
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync lib32stdc++6-9-dbg libx32stdc++6-9-dbg bison make cmake libgd-dev
```

3. Run ```bash
git clone https://github.com/guyezi/helloapp
```
 or 
 ```bash
git clone -b branch https://github.com/guyezi/helloapp
```
 to clone the source, and then ```bash cd lede ``` to enter the directory

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

4. Run

```bash
   ./scripts/feeds update -a
   ./scripts/feeds install -a
   make menuconfig
   ```

5. Run

 ```bash
   make -j8 download V=99
   make package/luci-app-ssr-plus/clean V=99
   make package/luci-app-ssr-plus/compile V=99
   make package/luci-app-ssr-plus/install V=99
   make package/luci-app-ssr-plus/{clean,compile,install} V=99
   make package/feeds/packages/luci-app-baidupcs-web/{clean,compile,install} V=99
   make tools/automake/compile
   make toolchain/{clean, compile, install}
   ```

6. 重编kernel: 

```bash
make target/linux/compile
make target/linux/install
make target/linux/{clean,compile,install}
```

7. 生成 `Packages` `Packages.gz` `Packages.manifest` :

```bash
make package/index
ipkg-make-index.sh . 2>&1 > Packages
gzip -9c Packages > Packages.gz 
```


