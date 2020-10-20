---
title: Linux에 PowerShell 설치
description: 다양한 Linux 배포에 PowerShell을 설치하는 방법에 대한 정보
ms.date: 07/30/2020
ms.openlocfilehash: f35366b5b1a0f54ce2c90d0e3cba59be7b9ce82c
ms.sourcegitcommit: 2ca12827dc64198b4263e8873a45b9466f22a67c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92079798"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="995a6-103">Linux에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="995a6-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="995a6-104">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="995a6-105">패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="995a6-106">[미리 보기 릴리스](#installing-preview-releases)를 설치한 경우 `pwsh-preview`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-107">PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="995a6-108">`/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="995a6-109">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="995a6-110">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell 맞춤 패키지][snap]를 사용하여 PowerShell을 설치해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="995a6-111">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성 패키지를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="995a6-112">공식적으로 지원되는 릴리스</span><span class="sxs-lookup"><span data-stu-id="995a6-112">Officially supported releases</span></span>

- <span data-ttu-id="995a6-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="995a6-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="995a6-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="995a6-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="995a6-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="995a6-115">Debian 8</span></span>
- <span data-ttu-id="995a6-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="995a6-116">Debian 9</span></span>
- <span data-ttu-id="995a6-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="995a6-117">Debian 10</span></span>
- <span data-ttu-id="995a6-118">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="995a6-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="995a6-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="995a6-119">CentOS 7</span></span>
- <span data-ttu-id="995a6-120">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="995a6-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="995a6-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="995a6-121">Fedora 28</span></span>
- <span data-ttu-id="995a6-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="995a6-122">Fedora 29</span></span>
- <span data-ttu-id="995a6-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="995a6-123">Fedora 30</span></span>
- <span data-ttu-id="995a6-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="995a6-124">openSUSE 42.3</span></span>
- <span data-ttu-id="995a6-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="995a6-125">openSUSE Leap 15</span></span>

<span data-ttu-id="995a6-126">커뮤니티에서 지원되는 릴리스</span><span class="sxs-lookup"><span data-stu-id="995a6-126">Community supported releases</span></span>

- <span data-ttu-id="995a6-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="995a6-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="995a6-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="995a6-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="995a6-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="995a6-129">Arch Linux</span></span>
- <span data-ttu-id="995a6-130">Kali</span><span class="sxs-lookup"><span data-stu-id="995a6-130">Kali</span></span>
- <span data-ttu-id="995a6-131">Raspbian(실험적)</span><span class="sxs-lookup"><span data-stu-id="995a6-131">Raspbian (experimental)</span></span>

<span data-ttu-id="995a6-132">대체 설치 방법</span><span class="sxs-lookup"><span data-stu-id="995a6-132">Alternate install methods</span></span>

- <span data-ttu-id="995a6-133">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="995a6-133">Snap Package</span></span>
- <span data-ttu-id="995a6-134">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="995a6-134">Binary Archives</span></span>
- <span data-ttu-id="995a6-135">.NET 글로벌 도구</span><span class="sxs-lookup"><span data-stu-id="995a6-135">.NET Global tool</span></span>

<span data-ttu-id="995a6-136">현재 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="995a6-136">Not currently supported</span></span>

- <span data-ttu-id="995a6-137">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="995a6-137">Ubuntu 20.04</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-138">PowerShell은 .NET에서 지원되는 배포만 지원할 수 있음</span><span class="sxs-lookup"><span data-stu-id="995a6-138">PowerShell can only support the distributions that are supported by .NET.</span></span> <span data-ttu-id="995a6-139">지원되는 배포 목록은 [.NET Core 릴리스 정보][distros]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="995a6-139">See the [.NET Core release notes][distros] for a list of supported distributions.</span></span> <span data-ttu-id="995a6-140">.NET에서 지원되는 배포가 여기에 나열되지 않은 경우 배포에 대한 지원을 추가하도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-140">If there is a distribution supported by .NET that is not listed here, you can request that support for the distribution be added.</span></span> <span data-ttu-id="995a6-141">[배포 지원 요청][] 템플릿을 사용하여 요청을 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="995a6-141">Please file a request using the [Distribution Support Request][] template.</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="995a6-142">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="995a6-142">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="995a6-143">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="995a6-143">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="995a6-144">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-144">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="995a6-145">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-145">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
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

<span data-ttu-id="995a6-146">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-146">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="995a6-147">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-147">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="995a6-148">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="995a6-148">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="995a6-149">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-149">Download the Debian package `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="995a6-150">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-150">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="995a6-151">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-151">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="995a6-152">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-152">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="995a6-153">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="995a6-153">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="995a6-154">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="995a6-154">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="995a6-155">패키지 리포지토리를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="995a6-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="995a6-156">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-156">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="995a6-157">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-157">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
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

<span data-ttu-id="995a6-158">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-158">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="995a6-159">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-159">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="995a6-160">직접 다운로드를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="995a6-160">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="995a6-161">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-161">Download the Debian package `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="995a6-162">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-162">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="995a6-163">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-163">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="995a6-164">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-164">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="995a6-165">제거 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="995a6-165">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="995a6-166">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="995a6-166">Ubuntu 18.10</span></span>

<span data-ttu-id="995a6-167">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="995a6-168">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="995a6-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-169">Ubuntu 18.10은 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="995a6-169">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="995a6-170">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="995a6-170">Ubuntu 19.04</span></span>

<span data-ttu-id="995a6-171">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-171">Installation is supported via `snapd`.</span></span> <span data-ttu-id="995a6-172">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="995a6-172">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-173">Ubuntu 19.04는 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="995a6-173">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="995a6-174">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="995a6-174">Ubuntu 20.04</span></span>

<span data-ttu-id="995a6-175">Ubuntu 20.04는 LTS 릴리스입니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-175">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="995a6-176">PowerShell은 현재 이 버전을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-176">PowerShell does not currently support this version.</span></span> <span data-ttu-id="995a6-177">이 버전에 대한 지원은 PowerShell 7.1 릴리스에 대한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-177">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="995a6-178">Ubuntu 20.04에 대한 지원을 원하는 경우 이 [요청](https://github.com/PowerShell/PowerShell/issues/12626)에 찬성하세요.</span><span class="sxs-lookup"><span data-stu-id="995a6-178">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="995a6-179">Debian 8</span><span class="sxs-lookup"><span data-stu-id="995a6-179">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="995a6-180">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="995a6-180">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="995a6-181">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-181">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="995a6-182">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-182">The preferred method is as follows:</span></span>

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

<span data-ttu-id="995a6-183">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-183">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="995a6-184">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-184">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="995a6-185">Debian 9</span><span class="sxs-lookup"><span data-stu-id="995a6-185">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="995a6-186">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="995a6-186">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="995a6-187">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="995a6-188">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-188">The preferred method is as follows:</span></span>

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

<span data-ttu-id="995a6-189">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-189">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="995a6-190">등록 후에는 `sudo apt-get install powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-190">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="995a6-191">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="995a6-191">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="995a6-192">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.3-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-192">Download the Debian package `powershell-lts_7.0.3-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="995a6-193">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-193">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="995a6-194">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="995a6-194">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="995a6-195">Debian 10</span><span class="sxs-lookup"><span data-stu-id="995a6-195">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-196">Debian 10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-196">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="995a6-197">패키지 리포지토리를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="995a6-197">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="995a6-198">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-198">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="995a6-199">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-199">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="995a6-200">직접 다운로드를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="995a6-200">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="995a6-201">[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.0.3-linux-x64.tar.gz`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-201">Download the tar.gz package `powershell-7.0.3-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="995a6-202">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-202">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="995a6-203">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="995a6-203">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-204">Alpine 3.9 및 3.10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-204">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="995a6-205">직접 다운로드를 통해 설치 - Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="995a6-205">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="995a6-206">[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.0.3-linux-alpine-x64.tar.gz`를 Alpine 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-206">Download the tar.gz package `powershell-7.0.3-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="995a6-207">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-207">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="995a6-208">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="995a6-208">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-209">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-209">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="995a6-210">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="995a6-210">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="995a6-211">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="995a6-212">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="995a6-213">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="995a6-214">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="995a6-214">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="995a6-215">[CentOS 7][]에서 [릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-215">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="995a6-216">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="995a6-217">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="995a6-218">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="995a6-218">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="995a6-220">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="995a6-220">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="995a6-221">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="995a6-221">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="995a6-222">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-222">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="995a6-223">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-223">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="995a6-224">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-224">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="995a6-225">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="995a6-225">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="995a6-226">[릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-226">Download the RPM package `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="995a6-227">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-227">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="995a6-228">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-228">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="995a6-229">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="995a6-229">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="995a6-230">openSUSE</span><span class="sxs-lookup"><span data-stu-id="995a6-230">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="995a6-231">설치 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="995a6-231">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="995a6-232">설치 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="995a6-232">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="995a6-233">제거 - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="995a6-233">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="995a6-234">Fedora</span><span class="sxs-lookup"><span data-stu-id="995a6-234">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-235">Fedora 28은 PowerShell 6.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-235">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-236">Fedora 29 및 30은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-236">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="995a6-237">패키지 리포지토리를 통해 설치(권장) - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="995a6-237">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="995a6-238">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-238">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="995a6-239">직접 다운로드를 통해 설치 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="995a6-239">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="995a6-240">[릴리스][] 페이지의 RPM 패키지 `powershell-7.0.3-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-240">Download the RPM package `powershell-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="995a6-241">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-241">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="995a6-242">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-242">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="995a6-243">제거 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="995a6-243">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="995a6-244">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="995a6-244">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-245">Arch Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-245">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="995a6-246">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-246">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="995a6-247">[최신 태깅 릴리스][arch-release]를 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-247">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="995a6-248">[최신 마스터 커밋][arch-git]을 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-248">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="995a6-249">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-249">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="995a6-250">AUR 패키지는 커뮤니티가 유지 관리하며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-250">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="995a6-251">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [Docker에서 PowerShell 사용](powershell-in-docker.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="995a6-251">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="995a6-253">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="995a6-253">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="995a6-254">snapd 가져오기</span><span class="sxs-lookup"><span data-stu-id="995a6-254">Getting snapd</span></span>

<span data-ttu-id="995a6-255">`snapd`는 snap을 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-255">`snapd` is required to run snaps.</span></span> <span data-ttu-id="995a6-256">[이 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-256">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="995a6-257">맞춤을 통해 설치</span><span class="sxs-lookup"><span data-stu-id="995a6-257">Installation via Snap</span></span>

<span data-ttu-id="995a6-258">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-258">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="995a6-259">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-259">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="995a6-260">미리 보기 버전을 설치하려면 다음 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-260">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="995a6-261">설치 후에는 맞춤이 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-261">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="995a6-262">`sudo snap refresh powershell` 또는`sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-262">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="995a6-263">제거</span><span class="sxs-lookup"><span data-stu-id="995a6-263">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="995a6-264">또는</span><span class="sxs-lookup"><span data-stu-id="995a6-264">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="995a6-265">Kali</span><span class="sxs-lookup"><span data-stu-id="995a6-265">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-266">Kali Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-266">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="995a6-267">설치 - Kali</span><span class="sxs-lookup"><span data-stu-id="995a6-267">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="995a6-268">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="995a6-268">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="995a6-269">Raspbian</span><span class="sxs-lookup"><span data-stu-id="995a6-269">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="995a6-270">Raspbian 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-270">Raspbian support is experimental.</span></span>

<span data-ttu-id="995a6-271">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-271">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="995a6-272">[Pi Zero](https://github.com/dotnet/coreclr/issues/10605)등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR 및 PowerShell은 Pi 2 및 Pi 3 디바이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-272">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="995a6-273">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-273">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="995a6-274">설치 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="995a6-274">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="995a6-275">필요에 따라 심볼 링크를 만들어 `pwsh` 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-275">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="995a6-276">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="995a6-276">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="995a6-277">미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="995a6-277">Installing Preview Releases</span></span>

<span data-ttu-id="995a6-278">패키지 리포지토리를 통해 Linux용 PowerShell 미리 보기 버전을 설치하면 패키지 이름이 `powershell`에서 `powershell-preview`로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-278">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="995a6-279">직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-279">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="995a6-280">다음 표에는 다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-280">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="995a6-281">배포</span><span class="sxs-lookup"><span data-stu-id="995a6-281">Distribution(s)</span></span> |            <span data-ttu-id="995a6-282">안정적인 명령</span><span class="sxs-lookup"><span data-stu-id="995a6-282">Stable Command</span></span>            |               <span data-ttu-id="995a6-283">미리 보기 명령</span><span class="sxs-lookup"><span data-stu-id="995a6-283">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="995a6-284">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="995a6-284">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="995a6-285">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="995a6-285">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="995a6-286">Fedora</span><span class="sxs-lookup"><span data-stu-id="995a6-286">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="995a6-287">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="995a6-287">Install as a .NET Global tool</span></span>

<span data-ttu-id="995a6-288">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-288">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="995a6-289">dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-289">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="995a6-290">그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-290">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="995a6-291">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-291">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="995a6-292">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="995a6-292">Binary Archives</span></span>

<span data-ttu-id="995a6-293">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-293">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="995a6-294">종속성</span><span class="sxs-lookup"><span data-stu-id="995a6-294">Dependencies</span></span>

<span data-ttu-id="995a6-295">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-295">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="995a6-296">하지만 .NET Core 런타임의 경우 다양한 배포에서 여러 종속성이 필요하며, PowerShell도 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-296">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="995a6-297">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-297">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="995a6-298">OS</span><span class="sxs-lookup"><span data-stu-id="995a6-298">OS</span></span>                 | <span data-ttu-id="995a6-299">종속성</span><span class="sxs-lookup"><span data-stu-id="995a6-299">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="995a6-300">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="995a6-300">Ubuntu 16.04</span></span>       | <span data-ttu-id="995a6-301">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="995a6-301">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="995a6-302">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="995a6-302">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="995a6-303">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="995a6-303">Ubuntu 17.10</span></span>       | <span data-ttu-id="995a6-304">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="995a6-304">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="995a6-305">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="995a6-305">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="995a6-306">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="995a6-306">Ubuntu 18.04</span></span>       | <span data-ttu-id="995a6-307">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="995a6-307">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="995a6-308">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="995a6-308">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="995a6-309">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="995a6-309">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="995a6-310">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="995a6-310">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="995a6-311">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="995a6-311">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="995a6-312">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="995a6-312">Debian 9 (Stretch)</span></span> | <span data-ttu-id="995a6-313">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="995a6-313">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="995a6-314">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="995a6-314">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="995a6-315">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="995a6-315">CentOS 7</span></span> <br> <span data-ttu-id="995a6-316">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="995a6-316">Oracle Linux 7</span></span> <br> <span data-ttu-id="995a6-317">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="995a6-317">RHEL 7</span></span> | <span data-ttu-id="995a6-318">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="995a6-318">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="995a6-319">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="995a6-319">openSUSE 42.3</span></span> | <span data-ttu-id="995a6-320">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="995a6-320">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="995a6-321">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="995a6-321">openSUSE Leap 15</span></span> | <span data-ttu-id="995a6-322">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="995a6-322">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="995a6-323">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="995a6-323">Fedora 27</span></span> <br> <span data-ttu-id="995a6-324">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="995a6-324">Fedora 28</span></span> | <span data-ttu-id="995a6-325">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="995a6-325">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="995a6-326">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-326">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="995a6-327">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-327">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="995a6-328">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="995a6-328">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="995a6-329">Linux</span><span class="sxs-lookup"><span data-stu-id="995a6-329">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="995a6-330">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="995a6-330">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="995a6-331">경로</span><span class="sxs-lookup"><span data-stu-id="995a6-331">Paths</span></span>

- <span data-ttu-id="995a6-332">`$PSHOME`은 `/opt/microsoft/powershell/7/`입니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-332">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="995a6-333">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-333">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="995a6-334">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-334">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="995a6-335">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-335">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="995a6-336">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-336">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="995a6-337">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-337">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="995a6-338">PSReadLine 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-338">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="995a6-339">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-339">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="995a6-340">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-340">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="995a6-341">설치 지원</span><span class="sxs-lookup"><span data-stu-id="995a6-341">Installation support</span></span>

<span data-ttu-id="995a6-342">Microsoft는 이 문서의 설치 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-342">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="995a6-343">다른 원본에서 사용 가능한 다른 설치 방법이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-343">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="995a6-344">관련 도구 및 방법이 유효하더라도 Microsoft에서는 해당 방법을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="995a6-344">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[배포 지원 요청]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
