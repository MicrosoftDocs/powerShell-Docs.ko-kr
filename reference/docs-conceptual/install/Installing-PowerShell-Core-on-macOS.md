---
title: MacOS에 PowerShell 설치
description: macOS에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 12/12/2018
ms.openlocfilehash: 2233bc01ee8c53087f79d83ca936c5a3800cfdba
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082767"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="ee766-103">MacOS에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="ee766-104">PowerShell은 macOS 10.12 이상을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="ee766-105">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="ee766-106">패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="ee766-107">PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="ee766-108">`/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="ee766-109">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [이진 아카이브](#binary-archives) 메서드를 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="ee766-110">Brew 정보</span><span class="sxs-lookup"><span data-stu-id="ee766-110">About Brew</span></span>

<span data-ttu-id="ee766-111">[Homebrew][brew]는 macOS용 기본 패키지 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="ee766-112">`brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="ee766-113">그렇지 않으면 [직접 다운로드](#installation-via-direct-download) 또는 [이진 아카이브](#binary-archives)를 이용해 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="ee766-114">macOS 10.12 이상에서 Homebrew를 통해 안정적인 최신 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="ee766-115">Brew에 대한 자세한 내용은 [Brew 정보](#about-brew)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee766-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="ee766-116">이제 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="ee766-117">최종적으로, 설치가 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="ee766-118">PowerShell의 새 버전이 릴리스되면 Homebrew의 Formula를 업데이트하고 PowerShell을 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="ee766-119">위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만 이때 PowerShell 셸을 종료하고 다시 시작하여 업그레이드를 완료하고 `$PSVersionTable`에 표시된 값을 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="ee766-120">macOS 10.12 이상에서 Homebrew를 통해 최신 미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="ee766-121">Brew에 대한 자세한 내용은 [Brew 정보](#about-brew)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee766-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="ee766-122">Homebrew를 설치한 후 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="ee766-123">먼저 [Cask-Versions][cask-versions] 패키지를 설치합니다. 그러면 cask 패키지의 대체 버전을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="ee766-124">이제 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="ee766-125">최종적으로, 설치가 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="ee766-126">PowerShell의 새 버전이 릴리스되면 Homebrew의 Formula를 업데이트하고 PowerShell을 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="ee766-127">위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만, 업그레이드를 완료하기 위해 PowerShell 셸을 종료하고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="ee766-128">그리고 `$PSVersionTable`에 표시된 값을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="ee766-129">직접 다운로드를 통해 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-129">Installation via Direct Download</span></span>

<span data-ttu-id="ee766-130">PKG 패키지 `powershell-6.2.0-osx-x64.pkg`를</span><span class="sxs-lookup"><span data-stu-id="ee766-130">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="ee766-131">[릴리스][] 페이지에서 macOS 머신으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="ee766-132">파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="ee766-133">[OpenSSL](#install-openssl)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="ee766-134">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="ee766-135">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="ee766-136">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="ee766-137">dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="ee766-138">그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="ee766-139">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="ee766-140">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="ee766-140">Binary Archives</span></span>

<span data-ttu-id="ee766-141">고급 배포 시나리오를 위해 macOS 플랫폼에 대해 PowerShell 이진 `tar.gz` 보관이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="ee766-142">macOS에서 이진 보관 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="ee766-143">[OpenSSL](#install-openssl)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="ee766-144">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="ee766-145">종속성 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="ee766-146">XCode 명령줄 도구 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="ee766-147">OpenSSL 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-147">Install OpenSSL</span></span>

<span data-ttu-id="ee766-148">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="ee766-149">MacPorts 또는 Brew를 통해 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="ee766-150">Brew를 통해 OpenSSL 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="ee766-151">Brew에 대한 자세한 내용은 [Brew 정보](#about-brew)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee766-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="ee766-152">OpenSSL을 설치하려면 `brew install openssl`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="ee766-153">MacPorts를 통해 OpenSSL 설치</span><span class="sxs-lookup"><span data-stu-id="ee766-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="ee766-154">[XCode 명령줄 도구](#install-xcode-command-line-tools)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="ee766-155">MacPorts를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-155">Install MacPorts.</span></span>
   <span data-ttu-id="ee766-156">지침이 필요한 경우 [설치 가이드](https://guide.macports.org/chunked/installing.macports.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee766-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="ee766-157">`sudo port selfupdate`를 실행하여 MacPorts를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="ee766-158">`sudo port upgrade outdated`를 실행하여 MacPorts 패키지를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="ee766-159">`sudo port install openssl`을 실행하여 OpenSSL을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="ee766-160">라이브러리를 연결하여 PowerShell에 대해 사용할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="ee766-161">PowerShell 제거</span><span class="sxs-lookup"><span data-stu-id="ee766-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="ee766-162">Homebrew를 사용하여 PowerShell을 설치한 경우 다음 명령을 사용하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="ee766-163">직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="ee766-164">추가 PowerShell 경로를 제거하려면 이 문서의 [경로](#paths) 섹션을 참조하고 `sudo rm`을 사용하여 경로를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="ee766-165">Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="ee766-166">경로</span><span class="sxs-lookup"><span data-stu-id="ee766-166">Paths</span></span>

* <span data-ttu-id="ee766-167">`$PSHOME`은 `/usr/local/microsoft/powershell/6.2.0/`입니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-167">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="ee766-168">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ee766-169">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ee766-170">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ee766-171">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ee766-172">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ee766-173">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ee766-174">프로필은 PowerShell의 호스트별 구성을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="ee766-175">따라서 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ee766-176">PowerShell은 macOS의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="ee766-177">macOS는 BSD에서 파생된 운영체제이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="ee766-178">따라서 `$PSHOME`은 `/usr/local/microsoft/powershell/6.2.0/`이며 기호화된 링크는 `/usr/local/bin/pwsh`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee766-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ee766-179">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="ee766-179">Additional Resources</span></span>

* <span data-ttu-id="ee766-180">[Homebrew 웹][brew]</span><span class="sxs-lookup"><span data-stu-id="ee766-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="ee766-181">[Homebrew Github 리포지토리][GitHub]</span><span class="sxs-lookup"><span data-stu-id="ee766-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="ee766-182">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="ee766-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
