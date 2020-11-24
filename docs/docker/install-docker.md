---
title: 'Installation of Docker'
---

Docker Engine is available on a variety of Linux platforms, macOS and Windows 10 through Docker Desktop, and as a static binary installation. 

## Linux

### Using convenience script

Easiest way to install Docker on Linux is using the convenience script. It is not recommended for production environments, because it requires `root` or `sudo` privileges and only installs latest stable Docker Engine - Community version along with all the dependencies. 

However, for development purposes, it provides an easy way to create environments quickly and non-interactively. This script can be used on many Linux distributions like Ubuntu, Debian, Cent OS, Fedora etc. as it attempts to detect your Linux distribution and version and configure your package management system for you. 

Install latest Docker container runtime using following command:

```bash
curl -sSL get.docker.com | sh
```

After the installation is finished, add current user to the "docker" group to use Docker as a non-root user with command:

```bash
sudo usermod -aG docker $USER
```

You would need to log out and login back in for this to take effect.

## Windows

Docker Desktop for Windows is the Community version of Docker for Microsoft Windows. The Docker Desktop installation includes Docker Engine, Docker CLI client, Docker Compose, Notary, Kubernetes, and Credential Helper. 

You can download Docker Desktop for Windows from Docker Hub. It can be downloaded from below location:

<https://hub.docker.com/editions/community/docker-ce-desktop-windows/>

Below are system requirements for installing Docker Desktop for Windows:
 
* Windows 10 64-bit: Pro, Enterprise, or Education (Build 16299 or later).
* For Windows 10 Home, Docker Desktop on Windows Home uses the WSL 2 backend. Docker Desktop on Windows Home is a full version of Docker Desktop for Linux container development.
* Hyper-V and Containers Windows features must be enabled on Pro, Enterprise, or Education (Build 16299 or later).
* WSL 2 feature must be enabled on Windows Home. For detailed instructions, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

The following hardware prerequisites are required to successfully run Client Hyper-V on Windows 10:

* 64 bit processor with Second Level Address Translation (SLAT)
* 4GB system RAM
* BIOS-level hardware virtualization support must be enabled in the BIOS settings. For more information, see Virtualization.
* For Windows Home, download and install the [Linux kernel update package](https://docs.microsoft.com/windows/wsl/wsl2-kernel).


