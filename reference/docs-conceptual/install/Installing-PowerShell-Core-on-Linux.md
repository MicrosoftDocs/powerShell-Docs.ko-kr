---
title: Linux에 PowerShell 설치
description: 다양한 Linux 배포에 PowerShell을 설치하는 방법에 대한 정보
ms.date: 03/09/2020
ms.openlocfilehash: 31da32b81dbbcf4b46fd5f0cd9d921f28f434763
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500545"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="2de20-103">Linux에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="2de20-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="2de20-104">[Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [Alpine 3.9 및 3.10][alpine], [CentOS 7][cos], [Red Hat Enterprise Linux(RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 28][fedora], [Fedora 29][fedora], [Fedora 30][fedora], [Arch Linux][arch]를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [Alpine 3.9 and 3.10][alpine], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 28][fedora], [Fedora 29][fedora], [Fedora 30][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="2de20-105">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell 맞춤 패키지][snap]를 사용하여 PowerShell을 설치해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="2de20-106">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성 패키지를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="2de20-107">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="2de20-108">패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="2de20-109">[미리 보기 릴리스](#installing-preview-releases)를 설치한 경우 `pwsh-preview`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-110">PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-110">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="2de20-111">`/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-111">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="2de20-112">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-112">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[alpine]: #alpine-39-and-310
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives


## <a name="installing-preview-releases"></a><span data-ttu-id="2de20-113">미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="2de20-113">Installing Preview Releases</span></span>

<span data-ttu-id="2de20-114">패키지 리포지토리를 통해 Linux용 PowerShell 미리 보기 버전을 설치하면 패키지 이름이 `powershell`에서 `powershell-preview`로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-114">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="2de20-115">직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-115">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="2de20-116">다음 표에는 다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-116">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="2de20-117">배포</span><span class="sxs-lookup"><span data-stu-id="2de20-117">Distribution(s)</span></span> |            <span data-ttu-id="2de20-118">안정적인 명령</span><span class="sxs-lookup"><span data-stu-id="2de20-118">Stable Command</span></span>            |               <span data-ttu-id="2de20-119">미리 보기 명령</span><span class="sxs-lookup"><span data-stu-id="2de20-119">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="2de20-120">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="2de20-120">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="2de20-121">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="2de20-121">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="2de20-122">Fedora</span><span class="sxs-lookup"><span data-stu-id="2de20-122">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a><span data-ttu-id="2de20-123">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2de20-123">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="2de20-124">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2de20-124">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="2de20-125">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-125">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2de20-126">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-126">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2de20-127">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-127">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2de20-128">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-128">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="2de20-129">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2de20-129">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="2de20-130">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-130">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2de20-131">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-131">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2de20-132">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-132">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="2de20-133">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-133">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="2de20-134">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2de20-134">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="2de20-135">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2de20-135">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="2de20-136">패키지 리포지토리를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2de20-136">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="2de20-137">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-137">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2de20-138">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-138">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2de20-139">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-139">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2de20-140">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-140">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="2de20-141">직접 다운로드를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2de20-141">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="2de20-142">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-142">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2de20-143">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-143">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2de20-144">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-144">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="2de20-145">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-145">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="2de20-146">제거 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2de20-146">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="2de20-147">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="2de20-147">Ubuntu 18.10</span></span>

<span data-ttu-id="2de20-148">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="2de20-149">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2de20-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-150">Ubuntu 18.10은 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="2de20-150">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="2de20-151">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="2de20-151">Ubuntu 19.04</span></span>

<span data-ttu-id="2de20-152">설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-152">Installation is supported via `snapd`.</span></span> <span data-ttu-id="2de20-153">지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2de20-153">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-154">Ubuntu 19.04는 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)로서 [커뮤니티 지원이 됩니다](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="2de20-154">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="2de20-155">Debian 8</span><span class="sxs-lookup"><span data-stu-id="2de20-155">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="2de20-156">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="2de20-156">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="2de20-157">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2de20-158">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-158">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2de20-159">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2de20-160">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-160">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="2de20-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="2de20-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="2de20-162">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2de20-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="2de20-163">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-163">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2de20-164">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-164">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2de20-165">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-165">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2de20-166">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-166">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="2de20-167">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2de20-167">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="2de20-168">[릴리스][] 페이지의 Debian 패키지 `powershell-lts_7.0.0-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-168">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="2de20-169">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-169">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="2de20-170">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2de20-170">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="2de20-171">Debian 10</span><span class="sxs-lookup"><span data-stu-id="2de20-171">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-172">Debian 10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-172">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="2de20-173">패키지 리포지토리를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="2de20-173">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="2de20-174">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-174">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2de20-175">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-175">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="2de20-176">직접 다운로드를 통해 설치 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="2de20-176">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="2de20-177">[릴리스][] 페이지의 tar.gz 패키지 `powershell_7.0.0-linux-x64.tar.gz`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-177">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="2de20-178">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-178">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="2de20-179">Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="2de20-179">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-180">Alpine 3.9 및 3.10은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-180">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="2de20-181">직접 다운로드를 통해 설치 - Alpine 3.9 및 3.10</span><span class="sxs-lookup"><span data-stu-id="2de20-181">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="2de20-182">[릴리스][] 페이지의 tar.gz 패키지 `powershell-7.0.0-linux-alpine-x64.tar.gz`를 Alpine 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-182">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="2de20-183">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-183">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="2de20-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2de20-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-185">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-185">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="2de20-186">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2de20-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="2de20-187">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-187">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2de20-188">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-188">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2de20-189">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-189">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="2de20-190">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2de20-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="2de20-191">[CentOS 7][]에서 [릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-191">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="2de20-192">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-192">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2de20-193">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-193">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="2de20-194">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2de20-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2de20-196">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2de20-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2de20-197">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2de20-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2de20-198">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-198">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2de20-199">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-199">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2de20-200">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-200">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2de20-201">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2de20-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2de20-202">[릴리스][] 페이지의 RPM 패키지 `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-202">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="2de20-203">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-203">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2de20-204">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-204">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2de20-205">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2de20-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="2de20-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2de20-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="2de20-207">설치 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2de20-207">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="2de20-208">설치 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2de20-208">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="2de20-209">제거 - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2de20-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="2de20-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="2de20-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-211">Fedora 28은 PowerShell 6.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-211">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-212">Fedora 29 및 30은 PowerShell 7.0 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-212">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="2de20-213">패키지 리포지토리를 통해 설치(권장) - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="2de20-213">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="2de20-214">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-214">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="2de20-215">직접 다운로드를 통해 설치 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="2de20-215">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="2de20-216">[릴리스][] 페이지의 RPM 패키지 `powershell-7.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-216">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="2de20-217">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-217">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2de20-218">다운로드 없이 바로 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-218">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="2de20-219">제거 - Fedora 28, 29 및 30</span><span class="sxs-lookup"><span data-stu-id="2de20-219">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="2de20-220">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="2de20-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-221">Arch Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-221">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="2de20-222">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="2de20-223">[최신 태깅 릴리스][arch-release]를 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="2de20-224">[최신 마스터 커밋][arch-git]을 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="2de20-225">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="2de20-226">AUR 패키지는 커뮤니티가 유지 관리하며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-226">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="2de20-227">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [Docker에서 PowerShell 사용](powershell-in-docker.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2de20-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="2de20-229">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="2de20-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="2de20-230">snapd 가져오기</span><span class="sxs-lookup"><span data-stu-id="2de20-230">Getting snapd</span></span>

<span data-ttu-id="2de20-231">`snapd`는 snap을 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-231">`snapd` is required to run snaps.</span></span> <span data-ttu-id="2de20-232">[이 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="2de20-233">맞춤을 통해 설치</span><span class="sxs-lookup"><span data-stu-id="2de20-233">Installation via Snap</span></span>

<span data-ttu-id="2de20-234">Linux용 PowerShell은 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-234">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="2de20-235">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-235">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="2de20-236">미리 보기 버전을 설치하려면 다음 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-236">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="2de20-237">설치 후에는 맞춤이 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-237">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="2de20-238">`sudo snap refresh powershell` 또는`sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-238">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="2de20-239">제거</span><span class="sxs-lookup"><span data-stu-id="2de20-239">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="2de20-240">또는</span><span class="sxs-lookup"><span data-stu-id="2de20-240">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="2de20-241">Kali</span><span class="sxs-lookup"><span data-stu-id="2de20-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-242">Kali Linux는 Microsoft에서 공식적으로 지원하지 않으며 커뮤니티에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-242">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="2de20-243">설치 - Kali</span><span class="sxs-lookup"><span data-stu-id="2de20-243">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="2de20-244">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="2de20-244">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="2de20-245">Raspbian</span><span class="sxs-lookup"><span data-stu-id="2de20-245">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="2de20-246">Raspbian 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-246">Raspbian support is experimental.</span></span>

<span data-ttu-id="2de20-247">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-247">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="2de20-248">[Pi Zero](https://github.com/dotnet/coreclr/issues/10605)등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR 및 PowerShell은 Pi 2 및 Pi 3 디바이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-248">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="2de20-249">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-249">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="2de20-250">설치 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2de20-250">Installation - Raspbian</span></span>

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

<span data-ttu-id="2de20-251">필요에 따라 심볼 링크를 만들어 `pwsh` 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-251">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="2de20-252">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2de20-252">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="2de20-253">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="2de20-253">Install as a .NET Global tool</span></span>

<span data-ttu-id="2de20-254">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-254">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="2de20-255">dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-255">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="2de20-256">그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-256">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="2de20-257">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-257">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="2de20-258">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="2de20-258">Binary Archives</span></span>

<span data-ttu-id="2de20-259">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="2de20-260">종속성</span><span class="sxs-lookup"><span data-stu-id="2de20-260">Dependencies</span></span>

<span data-ttu-id="2de20-261">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-261">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="2de20-262">하지만 .NET Core 런타임의 경우 다양한 배포에서 여러 종속성이 필요하며, PowerShell도 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-262">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="2de20-263">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="2de20-264">OS</span><span class="sxs-lookup"><span data-stu-id="2de20-264">OS</span></span>                 | <span data-ttu-id="2de20-265">종속성</span><span class="sxs-lookup"><span data-stu-id="2de20-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="2de20-266">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2de20-266">Ubuntu 16.04</span></span>       | <span data-ttu-id="2de20-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2de20-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2de20-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="2de20-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="2de20-269">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="2de20-269">Ubuntu 17.10</span></span>       | <span data-ttu-id="2de20-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2de20-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2de20-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="2de20-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="2de20-272">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2de20-272">Ubuntu 18.04</span></span>       | <span data-ttu-id="2de20-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2de20-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2de20-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="2de20-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="2de20-275">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="2de20-275">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="2de20-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2de20-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2de20-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="2de20-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="2de20-278">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="2de20-278">Debian 9 (Stretch)</span></span> | <span data-ttu-id="2de20-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2de20-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2de20-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="2de20-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="2de20-281">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2de20-281">CentOS 7</span></span> <br> <span data-ttu-id="2de20-282">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="2de20-282">Oracle Linux 7</span></span> <br> <span data-ttu-id="2de20-283">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="2de20-283">RHEL 7</span></span> | <span data-ttu-id="2de20-284">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="2de20-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="2de20-285">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2de20-285">openSUSE 42.3</span></span> | <span data-ttu-id="2de20-286">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="2de20-286">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="2de20-287">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2de20-287">openSUSE Leap 15</span></span> | <span data-ttu-id="2de20-288">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="2de20-288">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="2de20-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="2de20-289">Fedora 27</span></span> <br> <span data-ttu-id="2de20-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2de20-290">Fedora 28</span></span> | <span data-ttu-id="2de20-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="2de20-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="2de20-292">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-292">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="2de20-293">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="2de20-294">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="2de20-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="2de20-295">Linux</span><span class="sxs-lookup"><span data-stu-id="2de20-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="2de20-296">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="2de20-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="2de20-297">경로</span><span class="sxs-lookup"><span data-stu-id="2de20-297">Paths</span></span>

- <span data-ttu-id="2de20-298">`$PSHOME`은 `/opt/microsoft/powershell/7/`입니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-298">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="2de20-299">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="2de20-300">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="2de20-301">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="2de20-302">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="2de20-303">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-303">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="2de20-304">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="2de20-305">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="2de20-306">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2de20-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
