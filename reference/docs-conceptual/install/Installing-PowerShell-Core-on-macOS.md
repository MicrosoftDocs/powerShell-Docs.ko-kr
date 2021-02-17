---
title: MacOS에 PowerShell 설치
description: macOS에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 02/02/2021
ms.openlocfilehash: 3ae1fe0eb29b4d826221a2c11db19bc18c3efba7
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563211"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="ccd2a-103">MacOS에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="ccd2a-104">PowerShell 7.0 이상에는 macOS 10.13 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="ccd2a-105">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="ccd2a-106">패키지를 설치한 후 실행하려면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd2a-107">PowerShell 7.1은 PowerShell Core 6.x 및 7.0을 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-107">PowerShell 7.1 is an in-place upgrade that removes PowerShell Core 6.x and 7.0.</span></span>
>
> <span data-ttu-id="ccd2a-108">`/usr/local/microsoft/powershell/6` 폴더가 `/usr/local/microsoft/powershell/7`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="ccd2a-109">이전 버전의 PowerShell Core를 PowerShell 7.1과 함께 실행해야 하는 경우 [이진 보관](#binary-archives) 메서드를 사용하여 원하는 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-109">If you need to run and older version of PowerShell core side-by-side with PowerShell 7.1, install the version you want using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="ccd2a-110">macOS에 PowerShell을 설치하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="ccd2a-111">다음 방법 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="ccd2a-112">Homebrew를 사용하여 설치.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-112">Install using Homebrew.</span></span> <span data-ttu-id="ccd2a-113">Homebrew는 macOS용 기본 패키지 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="ccd2a-114">[직접 다운로드](#installation-via-direct-download)를 통해 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="ccd2a-115">[이진 보관](#binary-archives)에서 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="ccd2a-116">PowerShell을 설치한 후 [OpenSSL](#installing-dependencies)을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="ccd2a-117">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="ccd2a-118">macOS 10.13 이상에서 Homebrew를 통해 안정적인 최신 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="ccd2a-119">`brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="ccd2a-120">이제 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-120">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell
```

<span data-ttu-id="ccd2a-121">최종적으로, 설치가 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="ccd2a-122">PowerShell의 새 버전이 릴리스되면 Homebrew의 Formula를 업데이트하고 PowerShell을 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="ccd2a-123">위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만 이때 PowerShell 셸을 종료하고 다시 시작하여 업그레이드를 완료하고 `$PSVersionTable`에 표시된 값을 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="ccd2a-124">macOS 10.13 이상에서 Homebrew를 통해 최신 미리 보기 릴리스 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="ccd2a-125">Homebrew를 설치한 후 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="ccd2a-126">먼저 [Cask-Versions][cask-versions] 패키지를 설치합니다. 그러면 cask 패키지의 대체 버전을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="ccd2a-127">이제 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-127">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell-preview
```

<span data-ttu-id="ccd2a-128">최종적으로, 설치가 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="ccd2a-129">PowerShell의 새 버전이 릴리스되면 Homebrew의 Formula를 업데이트하고 PowerShell을 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="ccd2a-130">위의 명령은 PowerShell(pwsh) 호스트 내에서 호출할 수 있지만, 업그레이드를 완료하기 위해 PowerShell 셸을 종료하고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="ccd2a-131">그리고 `$PSVersionTable`에 표시된 값을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="ccd2a-132">안정적인 LTS 버전의 경우 Homebrew tap 메서드를 사용하여 PowerShell을 설치하는 방법도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="ccd2a-133">이제 설치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="ccd2a-134">PowerShell의 새 버전이 릴리스되면 간단하게 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="ccd2a-135">cask 또는 tap 메서드를 사용하는지 여부에 관계없이 최신 버전의 PowerShell로 업데이트하는 경우 처음에 PowerShell을 설치하는 데 사용한 것과 동일한 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="ccd2a-136">다른 메서드를 사용하는 경우 새 pwsh 세션을 여는 데는 계속해서 이전 버전의 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="ccd2a-137">다른 메서드를 사용하기로 결정하면 [Homebrew 연결 메서드](https://docs.brew.sh/Manpage#link-ln-options-formula)를 사용하여 문제를 해결하는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="ccd2a-138">직접 다운로드를 통해 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-138">Installation via Direct Download</span></span>

<span data-ttu-id="ccd2a-139">[릴리스][] 페이지의 PKG 패키지 `powershell-7.1.2-osx-x64.pkg`를 macOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-139">Download the PKG package `powershell-7.1.2-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="ccd2a-140">파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-7.1.2-osx-x64.pkg -target /
```

<span data-ttu-id="ccd2a-141">[OpenSSL](#installing-dependencies)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="ccd2a-142">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="ccd2a-143">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="ccd2a-144">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="ccd2a-145">dotnet 도구 설치 프로그램은 `PATH` 환경 변수에 `~/.dotnet/tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="ccd2a-146">그러나 현재 실행 중인 셸에는 `PATH`가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="ccd2a-147">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="ccd2a-148">[OpenSSL](#installing-dependencies)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="ccd2a-149">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="ccd2a-150">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="ccd2a-150">Binary Archives</span></span>

<span data-ttu-id="ccd2a-151">고급 배포 시나리오를 위해 macOS 플랫폼에 대해 PowerShell 이진 `tar.gz` 보관이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="ccd2a-152">해당 메서드를 사용하여 설치하는 경우 모든 종속성도 수동으로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="ccd2a-153">[OpenSSL](#installing-dependencies)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="ccd2a-154">OpenSSL은 PowerShell 원격 기능 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="ccd2a-155">macOS에서 이진 보관 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-155">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.2/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="ccd2a-156">종속성 설치</span><span class="sxs-lookup"><span data-stu-id="ccd2a-156">Installing dependencies</span></span>

<span data-ttu-id="ccd2a-157">OpenSSL은 PowerShell 원격 및 CIM 작업에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-157">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="ccd2a-158">필요한 경우 MacPorts를 통해 OpenSSL를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-158">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd2a-159">MacPorts 및 Homebrew는 동일한 시스템에서 함께 사용될 경우 문제가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-159">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="ccd2a-160">그러나 Homebrew에는 OpenSSL 1.0용 패키지가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-160">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="ccd2a-161">자세한 내용은 [MacPorts FAQ](https://trac.macports.org/wiki/FAQ)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-161">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="ccd2a-162">Xcode 명령줄 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-162">Install the Xcode command-line tools.</span></span> <span data-ttu-id="ccd2a-163">MacPorts에는 Xcode 도구가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-163">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="ccd2a-164">MacPorts를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-164">Install MacPorts.</span></span> <span data-ttu-id="ccd2a-165">지침이 필요한 경우 [설치 가이드](https://www.macports.org/install.php)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-165">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="ccd2a-166">`sudo port selfupdate`를 실행하여 MacPorts를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-166">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="ccd2a-167">`sudo port upgrade outdated`를 실행하여 MacPorts 패키지를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-167">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="ccd2a-168">`sudo port install openssl10`을 실행하여 OpenSSL을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-168">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="ccd2a-169">라이브러리를 연결하여 PowerShell에 대해 사용할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-169">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="ccd2a-170">PowerShell 제거</span><span class="sxs-lookup"><span data-stu-id="ccd2a-170">Uninstalling PowerShell</span></span>

<span data-ttu-id="ccd2a-171">Homebrew를 사용하여 PowerShell을 설치한 경우 다음 명령을 사용하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-171">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="ccd2a-172">직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-172">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="ccd2a-173">추가 PowerShell 경로를 제거하려면 이 문서의 [경로](#paths) 섹션을 참조하고 `sudo rm`을 사용하여 경로를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-173">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd2a-174">Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-174">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="ccd2a-175">경로</span><span class="sxs-lookup"><span data-stu-id="ccd2a-175">Paths</span></span>

- <span data-ttu-id="ccd2a-176">`$PSHOME`은 `/usr/local/microsoft/powershell/7.1.2/`입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.2/`</span></span>
- <span data-ttu-id="ccd2a-177">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-177">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="ccd2a-178">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-178">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="ccd2a-179">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-179">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="ccd2a-180">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-180">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="ccd2a-181">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-181">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="ccd2a-182">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-182">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ccd2a-183">프로필은 PowerShell의 호스트별 구성을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-183">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="ccd2a-184">따라서 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-184">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ccd2a-185">PowerShell은 macOS의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-185">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="ccd2a-186">macOS는 BSD에서 파생된 운영체제이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-186">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="ccd2a-187">따라서 `$PSHOME`은 `/usr/local/microsoft/powershell/7.1.2/`이며 기호화된 링크는 `/usr/local/bin/pwsh`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-187">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.2/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="ccd2a-188">설치 지원</span><span class="sxs-lookup"><span data-stu-id="ccd2a-188">Installation support</span></span>

<span data-ttu-id="ccd2a-189">Microsoft는 이 문서의 설치 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-189">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="ccd2a-190">다른 원본에서 사용 가능한 다른 설치 방법이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-190">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="ccd2a-191">관련 도구 및 방법이 유효하더라도 Microsoft에서는 해당 방법을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd2a-191">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ccd2a-192">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="ccd2a-192">Additional Resources</span></span>

- <span data-ttu-id="ccd2a-193">[Homebrew 웹][brew]</span><span class="sxs-lookup"><span data-stu-id="ccd2a-193">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="ccd2a-194">[Homebrew Github 리포지토리][GitHub]</span><span class="sxs-lookup"><span data-stu-id="ccd2a-194">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="ccd2a-195">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="ccd2a-195">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[릴리스]: https://aka.ms/powershell-release?tag=stable
[releases]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
