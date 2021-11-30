Let's start!
---
1. First, install Ubuntu 64bit (Ubuntu 20.04 LTS x64).

2. Run `sudo apt-get update` in the terminal, and then run

```bash
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync lib32stdc++6-9-dbg libx32stdc++6-9-dbg bison make cmake libgd-dev
```

```bash
sudo apt-get install gcc g++ binutils patch bzip2 flex bison make autoconf gettext texinfo unzip sharutils subversion libncurses5-dev ncurses-term zlib1g-dev
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

6.  重编kernel: 

```bash
make target/linux/compile
make target/linux/install
make target/linux/{clean,compile,install}
```
7.  生成 `Packages` `Packages.gz` `Packages.manifest` :

```bash
make package/index
ipkg-make-index.sh . 2>&1 > Packages
gzip -9c Packages > Packages.gz 
```
8.  编译glibc
 
```bash
cd /usr/local
sudo wget https://ftp.gnu.org/gnu/glibc/glibc-2.34.tar.gz
sudo tar -zxvf glibc-2.34.tar.gz
```

```bash
cd /usr/local/glibc-2.34
su
mkdir build
cd build
../configure --prefix=/usr --disable-profile --enable-add-ons --with-headers=/usr/include --with-binutils=/usr/bin
make
make install
```
此时如果出现ls目录不能使用的情况，先解决命令不能使用问题。
LD_PRELOAD=/lib64/libc-2.34.so
设置软连接
```bash
rm /usr/lib64/libc.so.6
ln -s /usr/lib64/libc-2.17.so /usr/lib64/libc.so.6

```

