---
title: Linux에서 PowerShell Core 설치
description: 다양한 Linux 배포판에서 PowerShell Core를 설치하는 방법에 대한 정보
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68372188"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="2aed9-103">Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="2aed9-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="2aed9-104">[Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [RHEL(Red Hat Enterprise Linux) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] 및 [Arch Linux][arch]를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="2aed9-105">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell 맞춤 패키지][snap]를 사용하여 PowerShell을 설치해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="2aed9-106">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="2aed9-107">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="2aed9-108">패키지가 설치된 후 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-108">After the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="2aed9-109">미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="2aed9-109">Installing Preview Releases</span></span>

<span data-ttu-id="2aed9-110">패키지 리포지토리를 통해 Linux용 PowerShell Core 미리 보기 버전을 설치하려면 패키지 이름을 `powershell`에서 `powershell-preview`로 변경하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="2aed9-111">직접 다운로드를 통한 설치는 파일 이름 외에는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="2aed9-112">다음 표에는 다양한 패키지 관리자를 사용하여 안정적인/미리 보기 버전 패키지를 설치하는 명령이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="2aed9-113">배포</span><span class="sxs-lookup"><span data-stu-id="2aed9-113">Distribution(s)</span></span>|<span data-ttu-id="2aed9-114">안정적인 명령</span><span class="sxs-lookup"><span data-stu-id="2aed9-114">Stable Command</span></span> | <span data-ttu-id="2aed9-115">미리 보기 명령</span><span class="sxs-lookup"><span data-stu-id="2aed9-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="2aed9-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="2aed9-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="2aed9-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="2aed9-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="2aed9-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="2aed9-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="2aed9-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="2aed9-120">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="2aed9-121">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2aed9-122">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2aed9-123">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2aed9-124">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="2aed9-125">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="2aed9-126">[릴리스][] 페이지의 Debian 패키지 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2aed9-127">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2aed9-128">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="2aed9-129">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="2aed9-130">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="2aed9-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="2aed9-132">패키지 리포지토리를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="2aed9-133">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2aed9-134">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2aed9-135">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2aed9-136">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="2aed9-137">직접 다운로드를 통해 설치 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="2aed9-138">[릴리스][] 페이지의 Debian 패키지 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2aed9-139">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2aed9-140">`dpkg -i` 명령은 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="2aed9-141">다음 명령인 `apt-get install -f`는 이러한 문제를 해결한 다음, PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="2aed9-142">제거 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="2aed9-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="2aed9-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="2aed9-144">18.10이 [중간 릴리스](https://www.ubuntu.com/about/release-cycle)이므로 [커뮤니티 지원](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="2aed9-145">18.10의 설치는 `snapd`를 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="2aed9-146">전체 지침은 [맞춤 패키지][snap]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2aed9-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="2aed9-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="2aed9-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="2aed9-148">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="2aed9-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="2aed9-149">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2aed9-150">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2aed9-151">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2aed9-152">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="2aed9-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="2aed9-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="2aed9-154">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2aed9-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="2aed9-155">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 패키지 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2aed9-156">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2aed9-157">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2aed9-158">등록 후에는 `sudo apt-get upgrade powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="2aed9-159">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2aed9-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="2aed9-160">[릴리스][] 페이지의 Debian 패키지 `powershell_6.2.0-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="2aed9-161">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="2aed9-162">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2aed9-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="2aed9-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="2aed9-164">이 패키지는 Oracle Linux 7에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="2aed9-165">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="2aed9-166">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2aed9-167">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2aed9-168">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="2aed9-169">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="2aed9-170">[CentOS 7][]을 사용하여 [릴리스][] 페이지의 RPM 패키지 `powershell-6.2.0-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="2aed9-171">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2aed9-172">다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="2aed9-173">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2aed9-175">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2aed9-176">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2aed9-177">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2aed9-178">슈퍼 사용자로 Microsoft 리포지토리를 한 번 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2aed9-179">등록 후에는 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2aed9-180">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2aed9-181">[릴리스][] 페이지의 RPM 패키지 `powershell-6.2.0-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="2aed9-182">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2aed9-183">다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2aed9-184">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="2aed9-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2aed9-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="2aed9-186">설치 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2aed9-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="2aed9-187">설치 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2aed9-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="2aed9-188">제거 - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2aed9-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="2aed9-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="2aed9-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="2aed9-190">Fedora 28은 PowerShell Core 6.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="2aed9-191">패키지 리포지토리를 통해 설치(권장) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2aed9-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="2aed9-192">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 공식 Microsoft 리포지토리에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="2aed9-193">직접 다운로드를 통해 설치 - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2aed9-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="2aed9-194">[릴리스][] 페이지의 RPM 패키지 `powershell-6.2.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="2aed9-195">그런 다음, 터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2aed9-196">다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="2aed9-197">제거 - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2aed9-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="2aed9-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="2aed9-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="2aed9-199">아치 리눅스 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-199">Arch support is experimental.</span></span>

<span data-ttu-id="2aed9-200">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="2aed9-201">[최신 태깅 릴리스][arch-release]를 사용하여 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="2aed9-202">[최신 마스터 커밋][arch-git]에서 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="2aed9-203">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="2aed9-204">AUR의 패키지는 커뮤니티에서 유지 관리되며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="2aed9-205">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 커뮤니티를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2aed9-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="2aed9-207">맞춤 패키지</span><span class="sxs-lookup"><span data-stu-id="2aed9-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="2aed9-208">snapd 가져오기</span><span class="sxs-lookup"><span data-stu-id="2aed9-208">Getting snapd</span></span>

<span data-ttu-id="2aed9-209">`snapd`는 snap을 실행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="2aed9-210">[이러한 지침](https://docs.snapcraft.io/core/install)을 사용하여 `snapd`를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="2aed9-211">맞춤을 통해 설치</span><span class="sxs-lookup"><span data-stu-id="2aed9-211">Installation via Snap</span></span>

<span data-ttu-id="2aed9-212">Linux용 PowerShell Core는 간편한 설치 및 업데이트를 위해 [맞춤 저장소](https://snapcraft.io/store)에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="2aed9-213">기본 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="2aed9-214">미리 보기 버전을 설치하려면 다음 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="2aed9-215">설치 후에는 맞춤이 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="2aed9-216">`sudo snap refresh powershell` 또는`sudo snap refresh powershell-preview`를 사용하여 업그레이드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="2aed9-217">제거</span><span class="sxs-lookup"><span data-stu-id="2aed9-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="2aed9-218">또는</span><span class="sxs-lookup"><span data-stu-id="2aed9-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="2aed9-219">Kali</span><span class="sxs-lookup"><span data-stu-id="2aed9-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="2aed9-220">설치 - Kali</span><span class="sxs-lookup"><span data-stu-id="2aed9-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="2aed9-221">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="2aed9-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="2aed9-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="2aed9-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="2aed9-223">Raspbian 지원은 실험적입니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="2aed9-224">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="2aed9-225">[Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 등의 다른 디바이스에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR 및 PowerShell Core는 Pi 2 및 Pi 3 디바이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="2aed9-226">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="2aed9-227">설치 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2aed9-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="2aed9-228">필요에 따라 심볼 링크를 만들어 `pwsh` 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="2aed9-229">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2aed9-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="2aed9-230">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="2aed9-230">Binary Archives</span></span>

<span data-ttu-id="2aed9-231">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 압축 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="2aed9-232">종속성</span><span class="sxs-lookup"><span data-stu-id="2aed9-232">Dependencies</span></span>

<span data-ttu-id="2aed9-233">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="2aed9-234">하지만 .NET Core 런타임의 경우 다양한 배포에서 여러 종속성이 필요하며, PowerShell도 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="2aed9-235">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="2aed9-236">OS</span><span class="sxs-lookup"><span data-stu-id="2aed9-236">OS</span></span>                 | <span data-ttu-id="2aed9-237">종속성</span><span class="sxs-lookup"><span data-stu-id="2aed9-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="2aed9-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="2aed9-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2aed9-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2aed9-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="2aed9-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="2aed9-241">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="2aed9-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="2aed9-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2aed9-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2aed9-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="2aed9-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="2aed9-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2aed9-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="2aed9-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2aed9-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2aed9-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="2aed9-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="2aed9-247">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="2aed9-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="2aed9-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2aed9-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2aed9-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="2aed9-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="2aed9-250">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="2aed9-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="2aed9-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2aed9-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2aed9-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="2aed9-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="2aed9-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-253">CentOS 7</span></span> <br> <span data-ttu-id="2aed9-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="2aed9-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="2aed9-255">RHEL 7</span></span> | <span data-ttu-id="2aed9-256">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="2aed9-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="2aed9-257">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2aed9-257">openSUSE 42.3</span></span> | <span data-ttu-id="2aed9-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="2aed9-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="2aed9-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2aed9-259">openSUSE Leap 15</span></span> | <span data-ttu-id="2aed9-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="2aed9-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="2aed9-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="2aed9-261">Fedora 27</span></span> <br> <span data-ttu-id="2aed9-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2aed9-262">Fedora 28</span></span> | <span data-ttu-id="2aed9-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="2aed9-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="2aed9-264">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="2aed9-265">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="2aed9-266">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="2aed9-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="2aed9-267">Linux</span><span class="sxs-lookup"><span data-stu-id="2aed9-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="2aed9-268">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="2aed9-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="2aed9-269">경로</span><span class="sxs-lookup"><span data-stu-id="2aed9-269">Paths</span></span>

* <span data-ttu-id="2aed9-270">`$PSHOME`은 `/opt/microsoft/powershell/6.2.0/`입니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="2aed9-271">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="2aed9-272">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="2aed9-273">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2aed9-274">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2aed9-275">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="2aed9-276">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="2aed9-277">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="2aed9-278">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2aed9-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
