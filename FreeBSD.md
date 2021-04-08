# FreeBSD Instructions

Couldn't get mingw64 toolchain to compile this...

Initially, I just installed "Windows services for linux" in a windows vm and compiled it from within wsl.

## WSL

### Requirements

1. Install Ubunutu WSL Bionic
2. in the ubuntu shell:

```bash
apt install automake libtool mingw64
```

```bash
cd ~
mkdir src
cd src
git clone https://github.com/xk2600/seamlessrdp.git
cd sealamlessrdp
git branch local
git checkout local
cd ServerExe
./autogen.sh
./configure --host=x86_64-w64-mingw32
make
mkdir /mnt/c/SeamlessRDP/
cp *.exe /mnt/c/SeamlessRDP/
```

Then from the FreeBSD Host in X:

```bash
RDP_SERVER_IP=192.168.0.10
rdesktop -A 'C:\SeamlessRDP\seamlessrdpshell.exe' -s 'notepad.exe' $RDP_SERVER_IP
```

