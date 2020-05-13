---
title: Linux에 PowerShell 설치
description: 다양한 Linux 배포에 PowerShell을 설치하는 방법에 대한 정보
ms.date: 03/09/2020
ms.openlocfilehash: e04d8a91999cd6e9b2d669230c7a1b412f11eeb8
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271902"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="108ae-103">Linux에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="108ae-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="108ae-104">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="108ae-105">패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="108ae-106">[미리 보기 릴리스](#installing-preview-releases)를 설치한 경우 `pwsh-preview`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-107">PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="108ae-108">`/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="108ae-109">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="108ae-110">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell 맞춤 패키지][snap]를 사용하여 PowerShell을 설치해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="108ae-111">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성 패키지를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="108ae-112">공식적으로 지원되는 릴리스</span><span class="sxs-lookup"><span data-stu-id="108ae-112">Officially supported releases</span></span>

- <span data-ttu-id="108ae-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="108ae-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="108ae-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="108ae-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="108ae-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="108ae-115">Debian 8</span></span>
- <span data-ttu-id="108ae-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="108ae-116">Debian 9</span></span>
- <span data-ttu-id="108ae-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="108ae-117">Debian 10</span></span>
- <span data-ttu-id="108ae-118">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="108ae-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="108ae-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="108ae-119">CentOS 7</span></span>
- <span data-ttu-id="108ae-120">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="108ae-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="108ae-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="108ae-121">Fedora 28</span></span>
- <span data-ttu-id="108ae-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="108ae-122">Fedora 29</span></span>
- <span data-ttu-id="108ae-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="108ae-123">Fedora 30</span></span>
- <span data-ttu-id="108ae-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="108ae-124">openSUSE 42.3</span></span>
- <span data-ttu-id="108ae-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="108ae-125">openSUSE Leap 15</span></span>

<span data-ttu-id="108ae-126">커뮤니티에서 지원되는 릴리스</span><span class="sxs-lookup"><span data-stu-id="108ae-126">Community supported releases</span></span>

- <span data-ttu-id="108ae-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="108ae-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="108ae-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="108ae-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="108ae-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="108ae-129">Arch Linux</span></span>
- <span data-ttu-id="108ae-130">Kali</span><span class="sxs-lookup"><span data-stu-id="108ae-130">Kali</span></span>
- <span data-ttu-id="108ae-131">Raspbian(실험적)</span><span class="sxs-lookup"><span data-stu-id="108ae-131">Raspbian (experimental)</span></span>

<span data-ttu-id="108ae-132">대체 설치 방법</span><span class="sxs-lookup"><span data-stu-id="108ae-132">Alternate install methods</span></span>

- <span data-ttu-id="108ae-133">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="108ae-133">Snap Package</span></span>
- <span data-ttu-id="108ae-134">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="108ae-134">Binary Archives</span></span>
- <span data-ttu-id="108ae-135">.NET 글로벌 도구</span><span class="sxs-lookup"><span data-stu-id="108ae-135">.NET Global tool</span></span>

<span data-ttu-id="108ae-136">현재 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="108ae-136">Not currently supported</span></span> 

- <span data-ttu-id="108ae-137">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="108ae-137">Ubuntu 20.04</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="108ae-138">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="108ae-138">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="108ae-139">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="108ae-139">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="108ae-140">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-140">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="108ae-141">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-141">The preferred method is as follows:</span></span>

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

<span data-ttu-id="108ae-142">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-142">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="108ae-143">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-143">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="108ae-144">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="108ae-144">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="108ae-145">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-145">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="108ae-146">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-146">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="108ae-147">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-147">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="108ae-148">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-148">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="108ae-149">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="108ae-149">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="108ae-150">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="108ae-150">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="108ae-151">패키지 리포지토리를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="108ae-151">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="108ae-152">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-152">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="108ae-153">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-153">The preferred method is as follows:</span></span>

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

<span data-ttu-id="108ae-154">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-154">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="108ae-155">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-155">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="108ae-156">직접 다운로드를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="108ae-156">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="108ae-157">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-157">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="108ae-158">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-158">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="108ae-159">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-159">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="108ae-160">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-160">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="108ae-161">제거 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="108ae-161">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="108ae-162">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="108ae-162">Ubuntu 18.10</span></span>

<span data-ttu-id="108ae-163">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-163">Installation is supported via `snapd`.</span></span> <span data-ttu-id="108ae-164">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="108ae-164">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-165">Ubuntu 18.10은 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="108ae-165">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="108ae-166">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="108ae-166">Ubuntu 19.04</span></span>

<span data-ttu-id="108ae-167">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="108ae-168">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="108ae-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-169">Ubuntu 19.04는 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="108ae-169">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="108ae-170">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="108ae-170">Ubuntu 20.04</span></span>

<span data-ttu-id="108ae-171">Ubuntu 20.04는 LTS 릴리스입니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-171">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="108ae-172">PowerShell은 현재 이 버전을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-172">PowerShell does not currently support this version.</span></span> <span data-ttu-id="108ae-173">이 버전에 대한 지원은 PowerShell 7.1 릴리스에 대한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-173">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="108ae-174">Ubuntu 20.04에 대한 지원을 원하는 경우 이 [요청](https://github.com/PowerShell/PowerShell/issues/12626)에 찬성하세요.</span><span class="sxs-lookup"><span data-stu-id="108ae-174">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="108ae-175">Debian 8</span><span class="sxs-lookup"><span data-stu-id="108ae-175">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="108ae-176">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="108ae-176">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="108ae-177">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-177">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="108ae-178">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-178">The preferred method is as follows:</span></span>

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

<span data-ttu-id="108ae-179">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-179">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="108ae-180">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-180">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="108ae-181">Debian 9</span><span class="sxs-lookup"><span data-stu-id="108ae-181">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="108ae-182">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="108ae-182">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="108ae-183">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-183">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="108ae-184">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-184">The preferred method is as follows:</span></span>

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

<span data-ttu-id="108ae-185">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="108ae-186">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-186">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="108ae-187">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="108ae-187">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="108ae-188">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-188">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="108ae-189">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="108ae-190">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="108ae-190">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="108ae-191">Debian 10</span><span class="sxs-lookup"><span data-stu-id="108ae-191">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-192">Debian 10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-192">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="108ae-193">패키지 리포지토리를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="108ae-193">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="108ae-194">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-194">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="108ae-195">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-195">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="108ae-196">직접 다운로드를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="108ae-196">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="108ae-197">[릴리스][] 페이지의 tar.gz 패키지 `powershell_7.0.0-linux-x64.tar.gz`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-197">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="108ae-198">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-198">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="108ae-199">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="108ae-199">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-200">Alpine 3.9 및 3.10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-200">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="108ae-201">직접 다운로드를 통해 설치 - Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="108ae-201">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="108ae-202">[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.0.0-linux-alpine-x64.tar.gz`를 Alpine 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-202">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="108ae-203">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-203">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="108ae-204">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="108ae-204">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-205">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-205">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="108ae-206">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="108ae-206">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="108ae-207">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-207">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="108ae-208">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-208">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="108ae-209">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-209">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="108ae-210">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="108ae-210">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="108ae-211">[CentOS 7][]에서 [릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-211">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="108ae-212">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="108ae-213">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="108ae-214">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="108ae-214">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="108ae-216">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="108ae-216">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="108ae-217">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="108ae-217">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="108ae-218">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-218">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="108ae-219">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-219">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="108ae-220">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-220">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="108ae-221">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="108ae-221">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="108ae-222">[릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-222">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="108ae-223">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-223">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="108ae-224">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-224">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="108ae-225">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="108ae-225">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="108ae-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="108ae-226">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="108ae-227">설치 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="108ae-227">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="108ae-228">설치 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="108ae-228">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="108ae-229">제거 - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="108ae-229">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="108ae-230">Fedora</span><span class="sxs-lookup"><span data-stu-id="108ae-230">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-231">Fedora 28은 PowerShell 6.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-231">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-232">Fedora 29 및 30은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-232">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="108ae-233">패키지 리포지토리를 통해 설치(권장) - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="108ae-233">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="108ae-234">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-234">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="108ae-235">직접 다운로드를 통해 설치 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="108ae-235">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="108ae-236">[릴리스][] 페이지의 RPM 패키지 `powershell-7.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-236">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="108ae-237">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-237">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="108ae-238">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-238">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="108ae-239">제거 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="108ae-239">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="108ae-240">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="108ae-240">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-241">Arch Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-241">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="108ae-242">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-242">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="108ae-243">[최신 태깅 릴리스][arch-release]를 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-243">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="108ae-244">[최신 마스터 커밋][arch-git]을 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-244">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="108ae-245">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-245">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="108ae-246">AUR 패키지는 커뮤니티가 유지 관리하며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-246">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="108ae-247">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [Docker에서 PowerShell 사용](powershell-in-docker.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="108ae-247">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="108ae-249">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="108ae-249">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="108ae-250">snapd 가져오기</span><span class="sxs-lookup"><span data-stu-id="108ae-250">Getting snapd</span></span>

<span data-ttu-id="108ae-251">`snapd`는 snap을 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-251">`snapd` is required to run snaps.</span></span> <span data-ttu-id="108ae-252">[이 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-252">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="108ae-253">맞춤을 통해 설치</span><span class="sxs-lookup"><span data-stu-id="108ae-253">Installation via Snap</span></span>

<span data-ttu-id="108ae-254">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-254">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="108ae-255">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-255">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="108ae-256">미리 보기 버전을 설치하려면 다음 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-256">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="108ae-257">설치 후에는 맞춤이 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-257">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="108ae-258">`sudo snap refresh powershell` 또는`sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-258">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="108ae-259">제거</span><span class="sxs-lookup"><span data-stu-id="108ae-259">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="108ae-260">또는</span><span class="sxs-lookup"><span data-stu-id="108ae-260">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="108ae-261">Kali</span><span class="sxs-lookup"><span data-stu-id="108ae-261">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-262">Kali Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-262">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="108ae-263">설치 - Kali</span><span class="sxs-lookup"><span data-stu-id="108ae-263">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="108ae-264">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="108ae-264">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="108ae-265">Raspbian</span><span class="sxs-lookup"><span data-stu-id="108ae-265">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="108ae-266">Raspbian 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-266">Raspbian support is experimental.</span></span>

<span data-ttu-id="108ae-267">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-267">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="108ae-268">[Pi Zero](https://github.com/dotnet/coreclr/issues/10605)등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR 및 PowerShell은 Pi 2 및 Pi 3 디바이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-268">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="108ae-269">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-269">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="108ae-270">설치 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="108ae-270">Installation - Raspbian</span></span>

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

<span data-ttu-id="108ae-271">필요에 따라 심볼 링크를 만들어 `pwsh` 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-271">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="108ae-272">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="108ae-272">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="108ae-273">미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="108ae-273">Installing Preview Releases</span></span>

<span data-ttu-id="108ae-274">패키지 리포지토리를 통해 Linux용 PowerShell 미리 보기 버전을 설치하면 패키지 이름이 `powershell`에서 `powershell-preview`로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-274">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="108ae-275">직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-275">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="108ae-276">다음 표에는 다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-276">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="108ae-277">배포</span><span class="sxs-lookup"><span data-stu-id="108ae-277">Distribution(s)</span></span> |            <span data-ttu-id="108ae-278">안정적인 명령</span><span class="sxs-lookup"><span data-stu-id="108ae-278">Stable Command</span></span>            |               <span data-ttu-id="108ae-279">미리 보기 명령</span><span class="sxs-lookup"><span data-stu-id="108ae-279">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="108ae-280">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="108ae-280">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="108ae-281">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="108ae-281">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="108ae-282">Fedora</span><span class="sxs-lookup"><span data-stu-id="108ae-282">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="108ae-283">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="108ae-283">Install as a .NET Global tool</span></span>

<span data-ttu-id="108ae-284">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-284">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="108ae-285">dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-285">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="108ae-286">그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-286">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="108ae-287">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-287">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="108ae-288">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="108ae-288">Binary Archives</span></span>

<span data-ttu-id="108ae-289">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-289">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="108ae-290">종속성</span><span class="sxs-lookup"><span data-stu-id="108ae-290">Dependencies</span></span>

<span data-ttu-id="108ae-291">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-291">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="108ae-292">하지만 .NET Core 런타임의 경우 다양한 배포에서 여러 종속성이 필요하며, PowerShell도 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-292">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="108ae-293">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-293">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="108ae-294">OS</span><span class="sxs-lookup"><span data-stu-id="108ae-294">OS</span></span>                 | <span data-ttu-id="108ae-295">종속성</span><span class="sxs-lookup"><span data-stu-id="108ae-295">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="108ae-296">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="108ae-296">Ubuntu 16.04</span></span>       | <span data-ttu-id="108ae-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="108ae-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="108ae-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="108ae-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="108ae-299">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="108ae-299">Ubuntu 17.10</span></span>       | <span data-ttu-id="108ae-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="108ae-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="108ae-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="108ae-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="108ae-302">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="108ae-302">Ubuntu 18.04</span></span>       | <span data-ttu-id="108ae-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="108ae-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="108ae-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="108ae-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="108ae-305">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="108ae-305">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="108ae-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="108ae-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="108ae-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="108ae-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="108ae-308">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="108ae-308">Debian 9 (Stretch)</span></span> | <span data-ttu-id="108ae-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="108ae-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="108ae-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="108ae-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="108ae-311">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="108ae-311">CentOS 7</span></span> <br> <span data-ttu-id="108ae-312">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="108ae-312">Oracle Linux 7</span></span> <br> <span data-ttu-id="108ae-313">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="108ae-313">RHEL 7</span></span> | <span data-ttu-id="108ae-314">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="108ae-314">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="108ae-315">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="108ae-315">openSUSE 42.3</span></span> | <span data-ttu-id="108ae-316">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="108ae-316">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="108ae-317">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="108ae-317">openSUSE Leap 15</span></span> | <span data-ttu-id="108ae-318">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="108ae-318">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="108ae-319">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="108ae-319">Fedora 27</span></span> <br> <span data-ttu-id="108ae-320">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="108ae-320">Fedora 28</span></span> | <span data-ttu-id="108ae-321">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="108ae-321">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="108ae-322">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-322">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="108ae-323">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-323">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="108ae-324">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="108ae-324">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="108ae-325">Linux</span><span class="sxs-lookup"><span data-stu-id="108ae-325">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="108ae-326">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="108ae-326">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="108ae-327">경로</span><span class="sxs-lookup"><span data-stu-id="108ae-327">Paths</span></span>

- <span data-ttu-id="108ae-328">`$PSHOME`은 `/opt/microsoft/powershell/7/`입니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-328">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="108ae-329">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-329">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="108ae-330">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-330">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="108ae-331">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-331">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="108ae-332">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-332">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="108ae-333">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-333">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="108ae-334">PSReadLine 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-334">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="108ae-335">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-335">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="108ae-336">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="108ae-336">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
