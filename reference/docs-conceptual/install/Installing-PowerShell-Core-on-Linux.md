---
title: Linux에서 PowerShell Core 설치
description: 다양한 Linux 배포판에서 PowerShell Core를 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: 32d6c0e718ca798af2f6a5d796c3ca362e7befd9
ms.sourcegitcommit: 13e170e8bff29d3d5f854c874de88f53c5e5ef20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67829432"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="c4b48-103">Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="c4b48-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="c4b48-104">[Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9],
[CentOS 7][cos], [RHEL(Red Hat Enterprise Linux) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse],
[Fedora 27][fedora], [Fedora 28][fedora] 및 [Arch Linux][arch]를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9],
[CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse],
[Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="c4b48-105">공식적으로 지원되지 않는 Linux 배포판의 경우 [PowerShell Snap 패키지][snap]를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="c4b48-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="c4b48-106">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c4b48-107">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c4b48-108">패키지가 설치되면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="c4b48-109">미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="c4b48-109">Installing Preview Releases</span></span>

<span data-ttu-id="c4b48-110">패키지 리포지토리를 통해 Linux용 PowerShell Core 미리 보기 버전을 설치하려면 패키지 이름을 `powershell`에서 `powershell-preview`로 변경하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="c4b48-111">직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="c4b48-112">다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령들은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="c4b48-113">배포</span><span class="sxs-lookup"><span data-stu-id="c4b48-113">Distribution(s)</span></span>|<span data-ttu-id="c4b48-114">안정적인 명령</span><span class="sxs-lookup"><span data-stu-id="c4b48-114">Stable Command</span></span> | <span data-ttu-id="c4b48-115">미리 보기 명령</span><span class="sxs-lookup"><span data-stu-id="c4b48-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="c4b48-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="c4b48-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="c4b48-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="c4b48-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="c4b48-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="c4b48-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="c4b48-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c4b48-120">패키지 리포지토리를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c4b48-121">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c4b48-122">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c4b48-123">슈퍼 사용자로 Microsoft 리포지토리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="c4b48-124">그 이후에는 `sudo apt-get upgrade powershell`을 사용하여 설치를 업데이트하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c4b48-125">직접 다운로드를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c4b48-126">Debian 패키지 `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`를</span><span class="sxs-lookup"><span data-stu-id="c4b48-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="c4b48-127">[릴리스][] 페이지에서 Ubuntu 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c4b48-128">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c4b48-129">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c4b48-130">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c4b48-131">제거 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c4b48-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c4b48-133">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c4b48-134">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c4b48-135">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-135">This is the preferred method.</span></span>

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

<span data-ttu-id="c4b48-136">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c4b48-137">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c4b48-138">Debian 패키지 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`를</span><span class="sxs-lookup"><span data-stu-id="c4b48-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="c4b48-139">[릴리스][] 페이지에서 Ubuntu 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c4b48-140">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c4b48-141">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c4b48-142">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c4b48-143">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="c4b48-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="c4b48-145">패키지 리포지토리를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="c4b48-146">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c4b48-147">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-147">This is the preferred method.</span></span>

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

<span data-ttu-id="c4b48-148">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="c4b48-149">직접 다운로드를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="c4b48-150">Debian 패키지 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`를</span><span class="sxs-lookup"><span data-stu-id="c4b48-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="c4b48-151">[릴리스][] 페이지에서 Ubuntu 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c4b48-152">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c4b48-153">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c4b48-154">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="c4b48-155">제거 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="c4b48-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="c4b48-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="c4b48-157">18.10이 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)이므로 [커뮤니티 지원](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="c4b48-158">18.10의 설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="c4b48-159">전체 지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4b48-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="c4b48-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c4b48-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c4b48-161">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c4b48-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c4b48-162">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c4b48-163">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-163">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

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

<span data-ttu-id="c4b48-164">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="c4b48-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c4b48-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c4b48-166">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c4b48-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c4b48-167">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c4b48-168">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-168">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

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

<span data-ttu-id="c4b48-169">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c4b48-170">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c4b48-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c4b48-171">Debian 패키지 `powershell_6.2.0-1.debian.9_amd64.deb`를</span><span class="sxs-lookup"><span data-stu-id="c4b48-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="c4b48-172">[릴리스][] 페이지에서 Debian 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c4b48-173">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c4b48-174">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c4b48-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c4b48-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="c4b48-176">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c4b48-177">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c4b48-178">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c4b48-179">이 명령들은 관리자 계정으로 Microsoft 리포지토리를 추가합니다. 그 이후에는 `sudo yum update powershell`을 사용하여 업데이트하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c4b48-180">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c4b48-181">[CentOS 7][]을 사용하여 RPM 패키지 `powershell-6.2.0-1.rhel.7.x86_64.rpm`을</span><span class="sxs-lookup"><span data-stu-id="c4b48-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c4b48-182">[릴리스][] 페이지에서 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c4b48-183">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c4b48-184">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c4b48-185">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c4b48-187">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c4b48-188">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c4b48-189">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c4b48-190">이 명령들은 관리자 계정으로 Microsoft 리포지토리를 추가합니다. 그 이후에는 `sudo yum update powershell`을 사용하여 업데이트하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c4b48-191">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c4b48-192">RPM 패키지 `powershell-6.2.0-1.rhel.7.x86_64.rpm`을</span><span class="sxs-lookup"><span data-stu-id="c4b48-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c4b48-193">[릴리스][] 페이지에서 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c4b48-194">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c4b48-195">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c4b48-196">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="c4b48-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c4b48-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="c4b48-198">설치 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c4b48-198">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="c4b48-199">설치 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="c4b48-199">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="c4b48-200">제거 - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="c4b48-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="c4b48-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="c4b48-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="c4b48-202">Fedora 28은 PowerShell Core 6.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="c4b48-203">패키지 리포지토리를 통해 설치(권장) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c4b48-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c4b48-204">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="c4b48-205">직접 다운로드를 통해 설치 - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c4b48-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c4b48-206">RPM 패키지 `powershell-6.2.0-1.rhel.7.x86_64.rpm`을</span><span class="sxs-lookup"><span data-stu-id="c4b48-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c4b48-207">[릴리스][] 페이지에서 Fedora 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c4b48-208">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c4b48-209">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="c4b48-210">제거 - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c4b48-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c4b48-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="c4b48-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="c4b48-212">아치 리눅스 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-212">Arch support is experimental.</span></span>

<span data-ttu-id="c4b48-213">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c4b48-214">[최신 태깅 릴리스][arch-release]를 사용하여 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c4b48-215">[최신 마스터 커밋][arch-git]에서 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c4b48-216">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c4b48-217">AUR의 패키지는 커뮤니티에서 유지 관리되며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c4b48-218">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 커뮤니티를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4b48-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="c4b48-220">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="c4b48-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="c4b48-221">snapd 가져오기</span><span class="sxs-lookup"><span data-stu-id="c4b48-221">Getting snapd</span></span>

<span data-ttu-id="c4b48-222">`snapd`는 snap을 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="c4b48-223">[이러한 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="c4b48-224">맞춤을 통해 설치</span><span class="sxs-lookup"><span data-stu-id="c4b48-224">Installation via Snap</span></span>

<span data-ttu-id="c4b48-225">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="c4b48-226">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="c4b48-227">미리 보기 버전을 설치하려면 다음 방법을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c4b48-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="c4b48-228">설치 후 Snap은 자동으로 업그레이드하지만, `sudo snap refresh powershell` 또는 `sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="c4b48-229">제거</span><span class="sxs-lookup"><span data-stu-id="c4b48-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="c4b48-230">또는</span><span class="sxs-lookup"><span data-stu-id="c4b48-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="c4b48-231">Kali</span><span class="sxs-lookup"><span data-stu-id="c4b48-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="c4b48-232">설치 - Kali</span><span class="sxs-lookup"><span data-stu-id="c4b48-232">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c4b48-233">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="c4b48-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="c4b48-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c4b48-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="c4b48-235">Raspbian 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="c4b48-236">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="c4b48-237">또한 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR(및 PowerShell Core)은 Pi 2 및 Pi 3 디바이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="c4b48-238">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="c4b48-239">설치 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c4b48-239">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="c4b48-240">필요에 따라 심볼 링크를 만들어 “pwsh” 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c4b48-241">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c4b48-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c4b48-242">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="c4b48-242">Binary Archives</span></span>

<span data-ttu-id="c4b48-243">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c4b48-244">종속성</span><span class="sxs-lookup"><span data-stu-id="c4b48-244">Dependencies</span></span>

<span data-ttu-id="c4b48-245">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c4b48-246">하지만 .NET Core 런타임의 경우 다양한 배포판에 대한 여러 종속성이 필요하므로 PowerShell가 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c4b48-247">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="c4b48-248">OS</span><span class="sxs-lookup"><span data-stu-id="c4b48-248">OS</span></span>                 | <span data-ttu-id="c4b48-249">종속성</span><span class="sxs-lookup"><span data-stu-id="c4b48-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c4b48-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="c4b48-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c4b48-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c4b48-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c4b48-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c4b48-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="c4b48-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c4b48-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c4b48-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="c4b48-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c4b48-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c4b48-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="c4b48-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c4b48-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c4b48-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="c4b48-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c4b48-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c4b48-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="c4b48-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c4b48-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c4b48-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="c4b48-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="c4b48-262">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="c4b48-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c4b48-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c4b48-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c4b48-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c4b48-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c4b48-265">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="c4b48-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c4b48-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c4b48-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c4b48-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="c4b48-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c4b48-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-268">CentOS 7</span></span> <br> <span data-ttu-id="c4b48-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="c4b48-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c4b48-270">RHEL 7</span></span> | <span data-ttu-id="c4b48-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="c4b48-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c4b48-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c4b48-272">openSUSE 42.3</span></span> | <span data-ttu-id="c4b48-273">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="c4b48-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="c4b48-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="c4b48-274">openSUSE Leap 15</span></span> | <span data-ttu-id="c4b48-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="c4b48-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="c4b48-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c4b48-276">Fedora 27</span></span> <br> <span data-ttu-id="c4b48-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c4b48-277">Fedora 28</span></span> | <span data-ttu-id="c4b48-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="c4b48-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c4b48-279">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c4b48-280">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c4b48-281">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="c4b48-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c4b48-282">Linux</span><span class="sxs-lookup"><span data-stu-id="c4b48-282">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="c4b48-283">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="c4b48-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c4b48-284">경로</span><span class="sxs-lookup"><span data-stu-id="c4b48-284">Paths</span></span>

* <span data-ttu-id="c4b48-285">`$PSHOME`은 `/opt/microsoft/powershell/6.2.0/`입니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="c4b48-286">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c4b48-287">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c4b48-288">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c4b48-289">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c4b48-290">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c4b48-291">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c4b48-292">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c4b48-293">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c4b48-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
