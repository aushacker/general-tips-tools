# Podman on Windows 10

Stephen Davies

Red Hat

5 Nov 2021

## Introduction

How to setup podman on Windows 10.

## Install Windows Subsystem for Linux

[Microsoft WSL2 installation instructions](https://docs.microsoft.com/en-us/windows/wsl/install)

1. Open a Windows command shell as Administrator
1. `wsl --install -d Ubuntu-20.04`
1. Reboot the PC
1. Enter userid and pwd

## Ubuntu Podman Installation

[Podman installation instructions](https://www.atlantic.net/dedicated-server-hosting/how-to-install-and-use-podman-on-ubuntu-20-04)

```
sudo -s
apt-get update -y
apt-get upgrade -y
apt-get install -y curl wget gnupg2
source /etc/os-release
sh -c "echo 'deb http://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_${VERSION_ID}/ /' > /etc/apt/sources.list.d/devel:kubic:libcontainers:stable.list"
wget -nv https://download.opensuse.org/repositories/devel:kubic:libcontainers:stable/xUbuntu_${VERSION_ID}/Release.key -O- | apt-key add -
apt-get update -qq -y
apt-get -qq --yes install podman
exit
podman run -it --rm docker.io/busybox echo 'Hello world'
```
