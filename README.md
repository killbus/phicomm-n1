# Phicomm-N1
Armian for Phicomm N1

## What do you need to get started?

- x64 machine with at least 2GB of memory and ~35GB of disk space for a VM, native OS
- Ubuntu Hirsute 21.04 x64 for native building
  - Hirsute is required for newer non-LTS releases.. ex: Bullseye, Sid, Groovy, Hirsute
  - If building for LTS releases.. ex: Focal, Bionic, Buster, it is possible to use Ubuntu 20.04 Focal, but it is not supported
- superuser rights (configured sudo or root access).

## How to start?
### Native and VirtualBox environments:
Login as root and run:
```text
apt-get -y -qq install git
git clone --depth 1 https://github.com/yunsur/phicomm-n1.git
cd phicomm-n1
```

### Build parameter examples

```text
./compile.sh \
BOARD=arm-64 \
BRANCH=current \
RELEASE=bullseye \
BUILD_MINIMAL=no \
BUILD_DESKTOP=no \
KERNEL_ONLY=no \
KERNEL_CONFIGURE=no \
COMPRESS_OUTPUTIMAGE=sha,img
```

  


## [User provided kernel config](https://docs.armbian.com/Developer-Guide_User-Configurations/#user-provided-kernel-config)  

If file userpatches/sources/$LINUXFAMILY.conf exists, it will be used in addition to the default one from config/sources. Look for the hint at the beginning of compilation process to select proper config file name. Please note that there are some exceptions for LINUXFAMILY like sunxi (32-bit mainline sunxi) and sunxi64 (64-bit mainline sunxi)

Example:

`[ o.k. ] Adding user provided sunxi64 overrides`

<pre><code><del>
## Change the docker volume `armbian-cache` and `armbian-ccache` location

As the cache may need a large space, you can change the volume manually.

Just modify the file `userpatches/config-docker.conf`, and change the line

example:

```
# mount 2 named volumes - for cacheable data and compiler cache
DOCKER_FLAGS+=(-v=$SRC/cache:/root/armbian/cache -v=$SRC/ccache:/root/.ccache)
```
</del></code></pre>
