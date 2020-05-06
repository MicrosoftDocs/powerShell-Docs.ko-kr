---
title: Linux에 PowerShell 설치
description: 다양한 Linux 배포에 PowerShell을 설치하는 방법에 대한 정보
ms.date: 03/09/2020
ms.openlocfilehash: 6ad637bd30e5e40ccc9532bae6f1171ecf79734a
ms.sourcegitcommit: e0a737961280026832cff9c658ed1468dc904e80
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605852"
---
# <a name="installing-powershell-on-linux"></a>Linux에 PowerShell 설치

모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다. 패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다. [미리 보기 릴리스](#installing-preview-releases)를 설치한 경우 `pwsh-preview`를 실행합니다.

> [!NOTE]
> PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.
>
> `/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.
>
> PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.

공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell 맞춤 패키지][snap]를 사용하여 PowerShell을 설치해 볼 수 있습니다. 또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성 패키지를 설치해야 합니다.

[snap]: #snap-package
[tar]: #binary-archives

공식적으로 지원되는 릴리스

- Ubuntu 16.04
- Ubuntu 18.04
- Debian 8
- Debian 9
- Debian 10
- Alpine 3.9 및 3.10
- CentOS 7
- Red Hat Enterprise Linux(RHEL) 7
- Fedora 28
- Fedora 29
- Fedora 30
- openSUSE 42.3
- openSUSE Leap 15

커뮤니티에서 지원되는 릴리스

- Ubuntu 18.10
- Ubuntu 19.04
- Arch Linux
- Kali
- Raspbian(실험적)

대체 설치 방법

- 맞춤 패키지
- 이진 아카이브
- .NET 글로벌 도구

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>패키지 리포지토리를 통해 설치 - Ubuntu 16.04

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.

기본 방법은 다음과 같습니다.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다. 등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.

### <a name="installation-via-direct-download---ubuntu-1604"></a>직접 다운로드를 통해 설치 - Ubuntu 16.04

[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다. 다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---ubuntu-1604"></a>제거 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>패키지 리포지토리를 통해 설치 - Ubuntu 18.04

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.

기본 방법은 다음과 같습니다.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다. 등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.

### <a name="installation-via-direct-download---ubuntu-1804"></a>직접 다운로드를 통해 설치 - Ubuntu 18.04

[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다. 다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---ubuntu-1804"></a>제거 - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

설치는 `snapd`를 통해 지원됩니다. 지침은 [맞춤 패키지][snap]를 참조하세요.

> [!NOTE]
> Ubuntu 18.10은 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).

## <a name="ubuntu-1904"></a>Ubuntu 19.04

설치는 `snapd`를 통해 지원됩니다. 지침은 [맞춤 패키지][snap]를 참조하세요.

> [!NOTE]
> Ubuntu 19.04는 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>패키지 리포지토리를 통해 설치 - Debian 8

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.

기본 방법은 다음과 같습니다.

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다. 등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>패키지 리포지토리를 통해 설치 - Debian 9

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.

기본 방법은 다음과 같습니다.

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다. 등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.

### <a name="installation-via-direct-download---debian-9"></a>직접 다운로드를 통해 설치 - Debian 9

[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>제거 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> Debian 10은 PowerShell 7.0 이상에서만 지원됩니다.

### <a name="installation-via-package-repository---debian-10"></a>패키지 리포지토리를 통해 설치 - Debian 10

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.

기본 방법은 다음과 같습니다.

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a>직접 다운로드를 통해 설치 - Debian 10

[릴리스][] 페이지의 tar.gz 패키지 `powershell_7.0.0-linux-x64.tar.gz`를 Debian 컴퓨터에 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a>Alpine 3.9 및 3.10

> [!NOTE]
> Alpine 3.9 및 3.10은 PowerShell 7.0 이상에서만 지원됩니다.

### <a name="installation-via-direct-download---alpine-39-and-310"></a>직접 다운로드를 통해 설치 - Alpine 3.9 및 3.10

[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.0.0-linux-alpine-x64.tar.gz`를 Alpine 컴퓨터에 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> 이 패키지는 Oracle Linux 7에서도 작동합니다.

### <a name="installation-via-package-repository-preferred---centos-7"></a>패키지 리포지토리를 통해 설치(권장) - CentOS 7

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다. 등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.

### <a name="installation-via-direct-download---centos-7"></a>직접 다운로드를 통해 설치 - CentOS 7

[CentOS 7][]에서 [릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

다운로드 없이 바로 RPM을 설치할 수 있습니다.

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>제거 - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux(RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다. 등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7

[릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

다운로드 없이 바로 RPM을 설치할 수 있습니다.

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>제거 - Red Hat Enterprise Linux(RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>설치 - openSUSE 42.3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>설치 - openSUSE Leap 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>제거 - openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28은 PowerShell 6.1 이상에서만 지원됩니다.

> [!NOTE]
> Fedora 29 및 30은 PowerShell 7.0 이상에서만 지원됩니다.

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>패키지 리포지토리를 통해 설치(권장) - Fedora 28, 29 및 30

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>직접 다운로드를 통해 설치 - Fedora 28, 29 및 30

[릴리스][] 페이지의 RPM 패키지 `powershell-7.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.

그런 다음, 터미널에서 다음 명령을 실행합니다.

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

다운로드 없이 바로 RPM을 설치할 수 있습니다.

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>제거 - Fedora 28, 29 및 30

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Arch Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.

PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.

- [최신 태깅 릴리스][arch-release]를 컴파일할 수 있습니다.
- [최신 마스터 커밋][arch-git]을 컴파일할 수 있습니다.
- [최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.

AUR 패키지는 커뮤니티가 유지 관리하며 공식적인 지원은 없습니다.

AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [Docker에서 PowerShell 사용](powershell-in-docker.md)을 참조하세요.

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>맞춤 패키지

### <a name="getting-snapd"></a>snapd 가져오기

`snapd`는 snap을 실행하는 데 필요합니다. [이 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.

### <a name="installation-via-snap"></a>맞춤을 통해 설치

Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.

기본 방법은 다음과 같습니다.

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

미리 보기 버전을 설치하려면 다음 방법을 사용합니다.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

설치 후에는 맞춤이 자동으로 업그레이드됩니다. `sudo snap refresh powershell` 또는`sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.

### <a name="uninstallation"></a>제거

```sh
sudo snap remove powershell
```

또는

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> Kali Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.

### <a name="installation---kali"></a>설치 - Kali

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>제거 - Kali

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian 지원은 실험적입니다.

현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.

[Pi Zero](https://github.com/dotnet/coreclr/issues/10605)등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR 및 PowerShell은 Pi 2 및 Pi 3 디바이스에서만 작동합니다.

[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.

### <a name="installation---raspbian"></a>설치 - Raspbian

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

필요에 따라 심볼 링크를 만들어 `pwsh` 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>제거 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a>미리 보기 릴리스 설치

패키지 리포지토리를 통해 Linux용 PowerShell 미리 보기 버전을 설치하면 패키지 이름이 `powershell`에서 `powershell-preview`로 변경됩니다.

직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.

다음 표에는 다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령이 들어 있습니다.

| 배포 |            안정적인 명령            |               미리 보기 명령                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| Ubuntu, Debian  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| CentOS, RedHat  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| Fedora          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a>.NET 전역 도구로 설치

[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.

```
dotnet tool install --global PowerShell
```

dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다. 그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다. 새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.

## <a name="binary-archives"></a>이진 아카이브

고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.

### <a name="dependencies"></a>종속성

PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다. 하지만 .NET Core 런타임의 경우 다양한 배포에서 여러 종속성이 필요하며, PowerShell도 그렇습니다.

다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.

| OS                 | 종속성 |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8(Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9(Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-libs, libicu |
| openSUSE 42.3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다. 예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>설치 - 이진 아카이브

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>이진 보관 제거

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>경로

- `$PSHOME`은 `/opt/microsoft/powershell/7/`입니다.
- 사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.
- 기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.
- 사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.
- 공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.
- 기본 모듈은 `$PSHOME/Modules`에서 읽습니다.
- PSReadLine 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.

프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.

PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
