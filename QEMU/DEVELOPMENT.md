## Acquire Source

To develop QEMU, building it from source code is necessary. The source code of QEMU could be cloned with command:
```bash
git clone https://github.com/qemu/qemu.git
```

## Prepare Environment

Ubuntu 24.04.2 on x86_64 machines is recommended as the developing environment. For basic building QEMU, install dependencies with command:
```bash
DEBIAN_FRONTEND="noninteractive" apt-get install --no-install-recommends -y \
    git python3 python3-pip ninja-build build-essential pkg-config curl bc jq \
    libslirp-dev libfdt-dev libglib2.0-dev libssl-dev libpixman-1-dev \
    flex bison
```

To avoid messing up with other versions of QEMU installed on the same host (probably installed through APT), it would be better to install those compiled artifacts to some other directories (like /opt/qemu).
```bash
# Setup directories to install customized QEMU
mkdir -p /opt/qemu
```

## Building QEMU

Enter the directory of QEMU source, then execute:
```bash
# prefix option sets where QEMU is going to be instaled
./configure --prefix=/opt/qemu
# Compile QEMU after making changes
make -j$(nproc)
# Install compiled QEMU to /opt/qemu
make install

# If this is the first time compiling QEMU, make sure to add
# /opt/qemu/bin to your PATH environment variable
# For bash:
# Edit ~/.bashrc, append `export PATH=$PATH:/opt/qemu/bin`
# Source ~/.bashrc to make it take effect
```
