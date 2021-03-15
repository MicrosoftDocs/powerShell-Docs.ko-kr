---
title: Linux에 PowerShell 설치
description: 다양한 Linux 배포에 PowerShell을 설치하는 방법에 대한 정보
ms.date: 02/02/2021
ms.openlocfilehash: ab075a3570695f5a58b7e7fbf968243a4ff45929
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195274"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="e8bab-103">Linux에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="e8bab-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="e8bab-104">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="e8bab-105">패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="e8bab-106">[미리 보기 릴리스](#installing-preview-releases)를 설치한 경우 `pwsh-preview`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-107">PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="e8bab-108">`/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="e8bab-109">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="e8bab-110">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell 맞춤 패키지][snap]를 사용하여 PowerShell을 설치해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="e8bab-111">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성 패키지를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="e8bab-112">PowerShell 7.1에 대해 공식적으로 지원되는 플랫폼 릴리스</span><span class="sxs-lookup"><span data-stu-id="e8bab-112">Officially supported platform releases for PowerShell 7.1</span></span>

- <span data-ttu-id="e8bab-113">Ubuntu 16.04/18.04/20.04(ARM64 포함)</span><span class="sxs-lookup"><span data-stu-id="e8bab-113">Ubuntu 16.04/18.04/20.04 (including ARM64)</span></span>
- <span data-ttu-id="e8bab-114">Ubuntu 19.10(맞춤 패키지를 통해)</span><span class="sxs-lookup"><span data-stu-id="e8bab-114">Ubuntu 19.10 (via Snap package)</span></span>
- <span data-ttu-id="e8bab-115">Debian 9/10</span><span class="sxs-lookup"><span data-stu-id="e8bab-115">Debian 9/10</span></span>
- <span data-ttu-id="e8bab-116">CentOS 및 RHEL 7/8</span><span class="sxs-lookup"><span data-stu-id="e8bab-116">CentOS and RHEL 7/8</span></span>
- <span data-ttu-id="e8bab-117">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="e8bab-117">Fedora 30</span></span>
- <span data-ttu-id="e8bab-118">Alpine 3.11+(ARM64 포함)</span><span class="sxs-lookup"><span data-stu-id="e8bab-118">Alpine 3.11+ (including ARM64)</span></span>

<span data-ttu-id="e8bab-119">PowerShell 7.0에 대해 공식적으로 지원되는 플랫폼 릴리스</span><span class="sxs-lookup"><span data-stu-id="e8bab-119">Officially supported platform releases for PowerShell 7.0</span></span>

- <span data-ttu-id="e8bab-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-120">Ubuntu 16.04</span></span>
- <span data-ttu-id="e8bab-121">Ubuntu 18.04 및 20.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-121">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="e8bab-122">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8bab-122">Debian 8</span></span>
- <span data-ttu-id="e8bab-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8bab-123">Debian 9</span></span>
- <span data-ttu-id="e8bab-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="e8bab-124">Debian 10</span></span>
- <span data-ttu-id="e8bab-125">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-125">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="e8bab-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-126">CentOS 7</span></span>
- <span data-ttu-id="e8bab-127">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-127">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="e8bab-128">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8bab-128">Fedora 28</span></span>
- <span data-ttu-id="e8bab-129">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="e8bab-129">Fedora 29</span></span>
- <span data-ttu-id="e8bab-130">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="e8bab-130">Fedora 30</span></span>
- <span data-ttu-id="e8bab-131">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e8bab-131">openSUSE 42.3</span></span>
- <span data-ttu-id="e8bab-132">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8bab-132">openSUSE Leap 15</span></span>

<span data-ttu-id="e8bab-133">커뮤니티에서 지원되는 릴리스</span><span class="sxs-lookup"><span data-stu-id="e8bab-133">Community supported releases</span></span>

- <span data-ttu-id="e8bab-134">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-134">Ubuntu 18.10</span></span>
- <span data-ttu-id="e8bab-135">Ubuntu 19.10 및 20.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-135">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="e8bab-136">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e8bab-136">Arch Linux</span></span>
- <span data-ttu-id="e8bab-137">Kali</span><span class="sxs-lookup"><span data-stu-id="e8bab-137">Kali</span></span>
- <span data-ttu-id="e8bab-138">Raspbian(실험적)</span><span class="sxs-lookup"><span data-stu-id="e8bab-138">Raspbian (experimental)</span></span>

<span data-ttu-id="e8bab-139">대체 설치 방법</span><span class="sxs-lookup"><span data-stu-id="e8bab-139">Alternate install methods</span></span>

- <span data-ttu-id="e8bab-140">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="e8bab-140">Snap Package</span></span>
- <span data-ttu-id="e8bab-141">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="e8bab-141">Binary Archives</span></span>
- <span data-ttu-id="e8bab-142">.NET 글로벌 도구</span><span class="sxs-lookup"><span data-stu-id="e8bab-142">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="e8bab-143">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-143">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e8bab-144">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-144">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e8bab-145">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-145">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-146">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-146">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of packages after we added packages.microsoft.com
sudo apt-get update
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="e8bab-147">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-147">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-148">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-148">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e8bab-149">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-149">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e8bab-150">[릴리스][] 페이지의 Debian 패키지 `powershell_7.1.2-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-150">Download the Debian package `powershell_7.1.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8bab-151">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-151">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8bab-152">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-152">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e8bab-153">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e8bab-154">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-154">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e8bab-155">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-155">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e8bab-156">패키지 리포지토리를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-156">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e8bab-157">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-158">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-158">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
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

<span data-ttu-id="e8bab-159">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-160">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-160">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e8bab-161">직접 다운로드를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-161">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e8bab-162">[릴리스][] 페이지의 Debian 패키지 `powershell_7.1.2-1.ubuntu.18.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-162">Download the Debian package `powershell_7.1.2-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8bab-163">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-163">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8bab-164">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-164">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e8bab-165">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-165">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e8bab-166">제거 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-166">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="e8bab-167">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-167">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="e8bab-168">패키지 리포지토리를 통해 설치 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-168">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="e8bab-169">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-169">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-170">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-170">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
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

<span data-ttu-id="e8bab-171">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-172">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-172">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="e8bab-173">직접 다운로드를 통해 설치 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-173">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="e8bab-174">[릴리스][] 페이지의 Debian 패키지 `powershell_7.1.2-1.ubuntu.20.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-174">Download the Debian package `powershell_7.1.2-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8bab-175">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8bab-176">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-176">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e8bab-177">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-177">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="e8bab-178">제거 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-178">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e8bab-179">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-179">Ubuntu 18.10</span></span>

<span data-ttu-id="e8bab-180">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-180">Installation is supported via `snapd`.</span></span> <span data-ttu-id="e8bab-181">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8bab-181">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-182">Ubuntu 18.10은 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="e8bab-182">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="e8bab-183">Ubuntu 19.10 및 20.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-183">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="e8bab-184">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-184">Installation is supported via `snapd`.</span></span> <span data-ttu-id="e8bab-185">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8bab-185">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-186">Ubuntu 19.10은 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="e8bab-186">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="e8bab-187">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8bab-187">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e8bab-188">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8bab-188">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e8bab-189">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-189">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-190">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-190">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e8bab-191">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-191">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-192">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-192">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="e8bab-193">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8bab-193">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e8bab-194">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8bab-194">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e8bab-195">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-195">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-196">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-196">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e8bab-197">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-197">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-198">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-198">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e8bab-199">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8bab-199">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e8bab-200">[릴리스][] 페이지의 Debian 패키지 `powershell_7.1.2-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-200">Download the Debian package `powershell_7.1.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e8bab-201">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-201">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e8bab-202">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8bab-202">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="e8bab-203">Debian 10</span><span class="sxs-lookup"><span data-stu-id="e8bab-203">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-204">Debian 10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-204">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="e8bab-205">패키지 리포지토리를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="e8bab-205">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="e8bab-206">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-206">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-207">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-207">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="e8bab-208">직접 다운로드를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="e8bab-208">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="e8bab-209">[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.1.2-linux-x64.tar.gz`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-209">Download the tar.gz package `powershell-7.1.2-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e8bab-210">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-210">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="e8bab-211">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-211">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-212">Alpine 3.9 및 3.10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-212">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="e8bab-213">직접 다운로드를 통해 설치 - Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-213">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="e8bab-214">[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.1.2-linux-alpine-x64.tar.gz`를 Alpine 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-214">Download the tar.gz package `powershell-7.1.2-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="e8bab-215">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-215">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="e8bab-216">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-216">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-217">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-217">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e8bab-218">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-218">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e8bab-219">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-219">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e8bab-220">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-220">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-221">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-221">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e8bab-222">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-222">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e8bab-223">[CentOS 7][]에서 [릴리스][] 페이지의 RPM 패키지 `powershell-7.1.2-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-223">Using [CentOS 7][], download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e8bab-224">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-224">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8bab-225">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-225">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e8bab-226">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-226">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8bab-228">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-228">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8bab-229">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-229">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e8bab-230">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-230">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e8bab-231">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-231">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e8bab-232">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-232">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8bab-233">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-233">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e8bab-234">[릴리스][] 페이지의 RPM 패키지 `powershell-7.1.2-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-234">Download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e8bab-235">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-235">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8bab-236">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-236">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8bab-237">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-237">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e8bab-238">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e8bab-238">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e8bab-239">설치 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e8bab-239">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e8bab-240">설치 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8bab-240">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e8bab-241">제거 - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8bab-241">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e8bab-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8bab-242">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-243">Fedora 28은 PowerShell 6.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-243">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-244">Fedora 29 및 30은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-244">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="e8bab-245">패키지 리포지토리를 통해 설치(권장) - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="e8bab-245">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="e8bab-246">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-246">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="e8bab-247">직접 다운로드를 통해 설치 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="e8bab-247">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="e8bab-248">[릴리스][] 페이지의 RPM 패키지 `powershell-7.1.2-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-248">Download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e8bab-249">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-249">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8bab-250">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-250">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="e8bab-251">제거 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="e8bab-251">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e8bab-252">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e8bab-252">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-253">Arch Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-253">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="e8bab-254">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-254">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="e8bab-255">[최신 태깅 릴리스][arch-release]를 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-255">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="e8bab-256">[최신 마스터 커밋][arch-git]을 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-256">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="e8bab-257">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-257">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e8bab-258">AUR 패키지는 커뮤니티가 유지 관리하며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-258">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="e8bab-259">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [Docker에서 PowerShell 사용](powershell-in-docker.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8bab-259">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e8bab-261">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="e8bab-261">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e8bab-262">snapd 가져오기</span><span class="sxs-lookup"><span data-stu-id="e8bab-262">Getting snapd</span></span>

<span data-ttu-id="e8bab-263">`snapd`는 snap을 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-263">`snapd` is required to run snaps.</span></span> <span data-ttu-id="e8bab-264">[이 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-264">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e8bab-265">맞춤을 통해 설치</span><span class="sxs-lookup"><span data-stu-id="e8bab-265">Installation via Snap</span></span>

<span data-ttu-id="e8bab-266">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-266">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="e8bab-267">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-267">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e8bab-268">미리 보기 버전을 설치하려면 다음 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-268">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e8bab-269">설치 후에는 맞춤이 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-269">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="e8bab-270">`sudo snap refresh powershell` 또는`sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-270">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e8bab-271">제거</span><span class="sxs-lookup"><span data-stu-id="e8bab-271">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e8bab-272">또는</span><span class="sxs-lookup"><span data-stu-id="e8bab-272">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e8bab-273">Kali</span><span class="sxs-lookup"><span data-stu-id="e8bab-273">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-274">Kali Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-274">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e8bab-275">설치 - Kali</span><span class="sxs-lookup"><span data-stu-id="e8bab-275">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e8bab-276">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="e8bab-276">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="support-for-arm-processors"></a><span data-ttu-id="e8bab-277">ARM 프로세서에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="e8bab-277">Support for Arm processors</span></span>

<span data-ttu-id="e8bab-278">PowerShell은 일부 Linux 배포에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-278">PowerShell can be installed on some Linux distributions.</span></span> <span data-ttu-id="e8bab-279">PowerShell은 ARM의 .NET 지원에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-279">PowerShell is dependent on .NET support of Arm.</span></span> <span data-ttu-id="e8bab-280">PowerShell은 다음 배포에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-280">PowerShell is supported on the following distributions:</span></span>

- <span data-ttu-id="e8bab-281">Alpine Linux v3.11+ - .NET은 ARM64를 지원하지만 지금은 PowerShell에 대해 설치 가능한 패키지가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-281">Alpine Linux v3.11+ - .NET supports Arm64 but there is no installable package for PowerShell at this time</span></span>
- <span data-ttu-id="e8bab-282">Raspbian - 아래 설치 지침 참조</span><span class="sxs-lookup"><span data-stu-id="e8bab-282">Raspbian - see the installation instructions below</span></span>
- <span data-ttu-id="e8bab-283">Debian v9+ - [이진 보관](#binary-archives) 설치 방법을 사용하여 ARM32 및 ARM64를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-283">Debian v9+ - supports Arm32 and Arm64 using the [Binary Archive](#binary-archives) installation method</span></span>
- <span data-ttu-id="e8bab-284">Ubuntu 20.10, 20.04, 18.04, 16.04 - [이진 보관](#binary-archives) 설치 방법을 사용하여 ARM32 및 ARM64를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-284">Ubuntu 20.10, 20.04, 18.04, 16.04 - supports Arm32 and Arm64 using the [Binary Archive](#binary-archives) installation method</span></span>

## <a name="raspbian"></a><span data-ttu-id="e8bab-285">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8bab-285">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e8bab-286">Raspbian 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-286">Raspbian support is experimental.</span></span>

<span data-ttu-id="e8bab-287">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-287">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e8bab-288">[Pi Zero](https://github.com/dotnet/coreclr/issues/10605)등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR 및 PowerShell은 Pi 2 및 Pi 3 디바이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-288">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e8bab-289">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-289">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e8bab-290">설치 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8bab-290">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.1.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="e8bab-291">필요에 따라 심볼 링크를 만들어 `pwsh` 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-291">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e8bab-292">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8bab-292">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="e8bab-293">미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="e8bab-293">Installing Preview Releases</span></span>

<span data-ttu-id="e8bab-294">패키지 리포지토리를 통해 Linux용 PowerShell 미리 보기 버전을 설치하면 패키지 이름이 `powershell`에서 `powershell-preview`로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-294">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e8bab-295">직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-295">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="e8bab-296">다음 표에는 다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-296">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="e8bab-297">배포</span><span class="sxs-lookup"><span data-stu-id="e8bab-297">Distribution(s)</span></span> |            <span data-ttu-id="e8bab-298">안정적인 명령</span><span class="sxs-lookup"><span data-stu-id="e8bab-298">Stable Command</span></span>            |               <span data-ttu-id="e8bab-299">미리 보기 명령</span><span class="sxs-lookup"><span data-stu-id="e8bab-299">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="e8bab-300">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e8bab-300">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="e8bab-301">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e8bab-301">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="e8bab-302">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8bab-302">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="e8bab-303">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="e8bab-303">Install as a .NET Global tool</span></span>

<span data-ttu-id="e8bab-304">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-304">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="e8bab-305">dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-305">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="e8bab-306">그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-306">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="e8bab-307">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-307">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="e8bab-308">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="e8bab-308">Binary Archives</span></span>

<span data-ttu-id="e8bab-309">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-309">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e8bab-310">종속성</span><span class="sxs-lookup"><span data-stu-id="e8bab-310">Dependencies</span></span>

<span data-ttu-id="e8bab-311">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-311">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="e8bab-312">하지만 .NET Core 런타임의 경우 다양한 배포에서 여러 종속성이 필요하며, PowerShell도 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-312">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="e8bab-313">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-313">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e8bab-314">OS</span><span class="sxs-lookup"><span data-stu-id="e8bab-314">OS</span></span>                 | <span data-ttu-id="e8bab-315">종속성</span><span class="sxs-lookup"><span data-stu-id="e8bab-315">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e8bab-316">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-316">Ubuntu 16.04</span></span>       | <span data-ttu-id="e8bab-317">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8bab-317">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8bab-318">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e8bab-318">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e8bab-319">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e8bab-319">Ubuntu 17.10</span></span>       | <span data-ttu-id="e8bab-320">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8bab-320">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8bab-321">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e8bab-321">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e8bab-322">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8bab-322">Ubuntu 18.04</span></span>       | <span data-ttu-id="e8bab-323">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8bab-323">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8bab-324">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e8bab-324">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e8bab-325">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="e8bab-325">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e8bab-326">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8bab-326">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8bab-327">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e8bab-327">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e8bab-328">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="e8bab-328">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e8bab-329">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8bab-329">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8bab-330">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e8bab-330">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e8bab-331">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-331">CentOS 7</span></span> <br> <span data-ttu-id="e8bab-332">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-332">Oracle Linux 7</span></span> <br> <span data-ttu-id="e8bab-333">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e8bab-333">RHEL 7</span></span> | <span data-ttu-id="e8bab-334">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e8bab-334">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e8bab-335">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e8bab-335">openSUSE 42.3</span></span> | <span data-ttu-id="e8bab-336">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e8bab-336">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e8bab-337">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8bab-337">openSUSE Leap 15</span></span> | <span data-ttu-id="e8bab-338">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e8bab-338">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e8bab-339">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e8bab-339">Fedora 27</span></span> <br> <span data-ttu-id="e8bab-340">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8bab-340">Fedora 28</span></span> | <span data-ttu-id="e8bab-341">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e8bab-341">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e8bab-342">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-342">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="e8bab-343">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-343">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e8bab-344">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="e8bab-344">Installation - Binary Archives</span></span>

<span data-ttu-id="e8bab-345">다음 예제에서는 x64 이진 보관을 설치하는 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-345">The following example shows the steps for installing the x64 binary archive.</span></span> <span data-ttu-id="e8bab-346">플랫폼의 프로세서 유형과 일치하는 올바른 이진 보관을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-346">You must choose the correct binary archive that matches the processor type for your platform.</span></span>

- <span data-ttu-id="e8bab-347">powershell-7.1.2-linux-arm32.tar.gz</span><span class="sxs-lookup"><span data-stu-id="e8bab-347">powershell-7.1.2-linux-arm32.tar.gz</span></span>
- <span data-ttu-id="e8bab-348">powershell-7.1.2-linux-arm64.tar.gz</span><span class="sxs-lookup"><span data-stu-id="e8bab-348">powershell-7.1.2-linux-arm64.tar.gz</span></span>
- <span data-ttu-id="e8bab-349">powershell-7.1.2-linux-x64.tar.gz</span><span class="sxs-lookup"><span data-stu-id="e8bab-349">powershell-7.1.2-linux-x64.tar.gz</span></span>

#### <a name="linux"></a><span data-ttu-id="e8bab-350">Linux</span><span class="sxs-lookup"><span data-stu-id="e8bab-350">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e8bab-351">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="e8bab-351">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e8bab-352">경로</span><span class="sxs-lookup"><span data-stu-id="e8bab-352">Paths</span></span>

- <span data-ttu-id="e8bab-353">`$PSHOME`은 `/opt/microsoft/powershell/7/`입니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-353">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="e8bab-354">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-354">User profiles are read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="e8bab-355">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-355">Default profiles are read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="e8bab-356">사용자 모듈은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-356">User modules are read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="e8bab-357">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-357">Shared modules are read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="e8bab-358">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-358">Default modules are read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="e8bab-359">PSReadLine 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-359">PSReadLine history is recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e8bab-360">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-360">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e8bab-361">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-361">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="e8bab-362">설치 지원</span><span class="sxs-lookup"><span data-stu-id="e8bab-362">Installation support</span></span>

<span data-ttu-id="e8bab-363">Microsoft는 이 문서의 설치 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-363">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="e8bab-364">다른 원본에서 사용 가능한 다른 설치 방법이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-364">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="e8bab-365">관련 도구 및 방법이 유효하더라도 Microsoft에서는 해당 방법을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8bab-365">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[릴리스]: https://aka.ms/PowerShell-Release?tag=stable
[releases]: https://aka.ms/PowerShell-Release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
