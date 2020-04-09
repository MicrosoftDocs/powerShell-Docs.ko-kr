---
title: Windows PowerShell 5.1에서 PowerShell 7로 마이그레이션
description: Windows 플랫폼의 PowerShell을 5.1에서 7로 업데이트.
ms.date: 03/25/2020
ms.openlocfilehash: e3881b1758f50119444969ad39541aec694cebe5
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500495"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="00494-103">Windows PowerShell 5.1에서 PowerShell 7로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="00494-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="00494-104">클라우드, 온-프레미스 및 하이브리드 환경에 맞게 설계된 PowerShell 7은 다수의 고급 기능과 [새로운 기능](What-s-New-in-PowerShell-70.md)을 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="00494-105">Windows PowerShell과 함께 설치 및 실행</span><span class="sxs-lookup"><span data-stu-id="00494-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="00494-106">기존 Windows PowerShell 모듈과의 호환성 향상</span><span class="sxs-lookup"><span data-stu-id="00494-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="00494-107">삼항 연산자 및 `ForEach-Object -Parallel`과 같은 새로운 언어 기능</span><span class="sxs-lookup"><span data-stu-id="00494-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="00494-108">성능 향상</span><span class="sxs-lookup"><span data-stu-id="00494-108">Improved performance</span></span>
- <span data-ttu-id="00494-109">SSH 기반 원격 기능</span><span class="sxs-lookup"><span data-stu-id="00494-109">SSH-based remoting</span></span>
- <span data-ttu-id="00494-110">플랫폼 간 상호 운용성</span><span class="sxs-lookup"><span data-stu-id="00494-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="00494-111">Docker 컨테이너에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="00494-111">Support for Docker containers</span></span>

<span data-ttu-id="00494-112">PowerShell 7은 Windows PowerShell과 함께 작동하므로 배포 전에 손쉽게 여러 버전을 테스트하고 버전 간 비교를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="00494-113">간편하고 빠르고 안전하게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="00494-114">실패.</span><span class="sxs-lookup"><span data-stu-id="00494-114">failure.</span></span>

<span data-ttu-id="00494-115">PowerShell 7이 지원되는 Windows 운영 체제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="00494-116">Windows 8.1 및 10</span><span class="sxs-lookup"><span data-stu-id="00494-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="00494-117">Windows Server 2012, 2012 R2, 2016, 2019</span><span class="sxs-lookup"><span data-stu-id="00494-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="00494-118">PowerShell 7은 macOS와 몇 가지 Linux 배포에서도 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="00494-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="00494-119">지원되는 운영 체제의 목록과 지원 수명 주기에 대한 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="00494-120">PowerShell 7 설치</span><span class="sxs-lookup"><span data-stu-id="00494-120">Installing PowerShell 7</span></span>

<span data-ttu-id="00494-121">유연성을 갖추고 IT, DevOps 엔지니어 및 개발자를 지원하기 위한 PowerShell 7 설치 옵션이 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="00494-122">대다수의 경우에 사용되는 설치 옵션을 요약하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="00494-123">[MSI 패키지](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)를 사용해 PowerShell 배포</span><span class="sxs-lookup"><span data-stu-id="00494-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="00494-124">[ZIP 패키지](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)를 사용해 PowerShell 배포</span><span class="sxs-lookup"><span data-stu-id="00494-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="00494-125">MSI 패키지는 [System Center Configuration Manager(SCCM)](/configmgr/apps/)와 같은 관리 제품으로 배포하고 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="00494-126">[GitHub 릴리스 페이지](https://github.com/PowerShell/PowerShell/releases)에서 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="00494-127">MSI 패키지를 배포하려면 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="00494-128">ZIP 패키지는 모든 사용자가 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="00494-129">ZIP 패키지는 전체 설치로 커밋하기 전에 PowerShell 7을 가장 쉽게 테스트 설치해볼 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="00494-130">PowerShell 7을 Windows PowerShell 5.1과 함께 사용</span><span class="sxs-lookup"><span data-stu-id="00494-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="00494-131">PowerShell 7은 Windows PowerShell 5.1과 함께 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="00494-132">다음 기능을 통해 PowerShell에 대한 투자가 보호되고 PowerShell 7로의 마이그레이션이 간편해집니다.</span><span class="sxs-lookup"><span data-stu-id="00494-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="00494-133">별도의 설치 경로와 실행 파일 이름</span><span class="sxs-lookup"><span data-stu-id="00494-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="00494-134">별도의 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="00494-134">Separate PSModulePath</span></span>
- <span data-ttu-id="00494-135">버전별 프로파일</span><span class="sxs-lookup"><span data-stu-id="00494-135">Separate profiles for each version</span></span>
- <span data-ttu-id="00494-136">향상된 모듈 호환성</span><span class="sxs-lookup"><span data-stu-id="00494-136">Improved module compatibility</span></span>
- <span data-ttu-id="00494-137">새로운 원격 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="00494-137">New remoting endpoints</span></span>
- <span data-ttu-id="00494-138">그룹 정책 지원</span><span class="sxs-lookup"><span data-stu-id="00494-138">Group policy support</span></span>
- <span data-ttu-id="00494-139">별도의 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="00494-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="00494-140">별도의 설치 경로와 실행 파일 이름</span><span class="sxs-lookup"><span data-stu-id="00494-140">Separate installation path and executable name</span></span>

<span data-ttu-id="00494-141">PowerShell 7은 새 디렉터리에 설치되므로 Windows PowerShell 5.1과 함께 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="00494-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="00494-142">버전별 설치 위치:</span><span class="sxs-lookup"><span data-stu-id="00494-142">Install locations by version:</span></span>

- <span data-ttu-id="00494-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="00494-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="00494-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="00494-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="00494-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="00494-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="00494-146">경로에 새 위치가 추가되면 Windows PowerShell 5.1 및 PowerShell 7을 모두 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="00494-147">PowerShell Core 6.x에서 PowerShell 7로 마이그레이션하는 경우 PowerShell 6이 제거되고 경로가 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="00494-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="00494-148">Windows PowerShell에서 PowerShell 실행 파일의 이름은 `powershell.exe`입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="00494-149">버전 6 이상에서 실행 파일의 이름은 `pwsh.exe`입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="00494-150">이름을 새로 지정하면 두 버전의 병렬 실행을 지원하기 쉬워집니다.</span><span class="sxs-lookup"><span data-stu-id="00494-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="00494-151">별도의 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="00494-151">Separate PSModulePath</span></span>

<span data-ttu-id="00494-152">기본적으로 Windows PowerShell 및 PowerShell 7은 다른 위치에 모듈을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="00494-153">PowerShell 7은 `$Env:PSModulePath` 환경 변수로 이 위치들을 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="00494-154">이름에 따라 모듈을 가져올 때 PowerShell은 `$Env:PSModulePath`에서 지정하는 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="00494-155">이를 통해 PowerShell 7은 코어 및 데스크톱 모듈을 모두 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="00494-156">설치 범위</span><span class="sxs-lookup"><span data-stu-id="00494-156">Install Scope</span></span>            |                <span data-ttu-id="00494-157">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="00494-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="00494-158">PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="00494-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="00494-159">PowerShell 모듈</span><span class="sxs-lookup"><span data-stu-id="00494-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="00494-160">사용자 설치</span><span class="sxs-lookup"><span data-stu-id="00494-160">User installed</span></span><br><span data-ttu-id="00494-161">AllUsers 범위</span><span class="sxs-lookup"><span data-stu-id="00494-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="00494-162">사용자 설치</span><span class="sxs-lookup"><span data-stu-id="00494-162">User installed</span></span><br><span data-ttu-id="00494-163">CurrentUser 범위</span><span class="sxs-lookup"><span data-stu-id="00494-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="00494-164">다음 예에서는 각 버전별로 `$Env:PSModulePath`의 기본값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00494-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="00494-165">Windows PowerShell 5.1의 경우:</span><span class="sxs-lookup"><span data-stu-id="00494-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="00494-166">PowerShell 7의 경우:</span><span class="sxs-lookup"><span data-stu-id="00494-166">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="00494-167">PowerShell 7에는 모듈 자동 로드를 제공하기 위한 Windows PowerShell 경로 및 PowerShell 7 경로가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="00494-168">PSModulePath 환경 변수 또는 설치된 사용자 지정 모듈 또는 애플리케이션을 변경한 경우 더 많은 경로가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="00494-169">자세한 내용은 [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences)의 `PSModulePath`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="00494-170">모듈에 대한 자세한 내용은 [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="00494-171">별도의 프로필</span><span class="sxs-lookup"><span data-stu-id="00494-171">Separate profiles</span></span>

<span data-ttu-id="00494-172">PowerShell 프로필은 PowerShell이 시작될 때 실행되는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="00494-173">이 스크립트에서는 명령, 별칭, 함수, 변수, 모듈, PowerShell 드라이브를 추가하여 환경을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="00494-174">프로필 스크립트 덕분에 이러한 사용자 지정 항목을 수동으로 다시 만들지 않고도 모든 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="00494-175">PowerShell 7에서 프로필의 위치를 가리키는 경로가 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="00494-176">Windows PowerShell 5.1에서 프로필의 위치는 `$HOME\Documents\WindowsPowerShell`입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="00494-177">PowerShell 7에서 프로필의 위치는 `$HOME\Documents\PowerShell`입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="00494-178">프로필 파일 이름도 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="00494-179">자세한 내용은 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="00494-180">PowerShell 7의 Windows PowerShell 5.1 모듈과의 호환성</span><span class="sxs-lookup"><span data-stu-id="00494-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="00494-181">Azure PowerShell, Active Directory 등 Windows PowerShell 5.1에서 사용하는 대부분의 모듈은 이미 PowerShell 7과 함께 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="00494-182">다른 팀과 협력하여 Microsoft Graph, Office 365 등 더 많은 모듈에 대해 기본 PowerShell 7 지원을 추가하는 작업을 계속 진행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="00494-183">지원되는 모듈의 현재 목록은 [PowerShell 7 모듈 호환성](/powershell/scripting/whats-new/module-compatibility)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="00494-184">또한 Windows에서는 호환되지 않는 모듈을 사용하는 사용자가 PowerShell 7로 쉽게 전환할 수 있도록 **UseWindowsPowerShell** 스위치를 `Import-Module`에 추가하였습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="00494-185">이 기능에 대한 자세한 내용은 [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="00494-186">PowerShell 원격 기능</span><span class="sxs-lookup"><span data-stu-id="00494-186">PowerShell Remoting</span></span>

<span data-ttu-id="00494-187">PowerShell 원격 기능을 사용하면 한 대 이상의 원격 컴퓨터에서 어떤 PowerShell 명령이라도 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="00494-188">원격 컴퓨터에서 영구 연결을 설정하고, 대화형 세션을 시작하고, 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="00494-189">WS-Management 원격 기능</span><span class="sxs-lookup"><span data-stu-id="00494-189">WS-Management remoting</span></span>

<span data-ttu-id="00494-190">Windows PowerShell 5.1 이하에서는 연결 협상 및 데이터 전송을 위해 WSMAN(WS-Management) 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="00494-191">WinRM(Windows 원격 관리)에서는 WSMAN 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="00494-192">WinRM이 사용하도록 설정된 경우 PowerShell 7에서는 원격 연결을 위해 `Microsoft.PowerShell`이라는 이름의 기존 Windows PowerShell 5.1 엔드포인트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="00494-193">자체 엔드포인트를 포함하도록 PowerShell 7을 업데이트하려면 `Enable-PSRemoting` cmdlet을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="00494-194">특정 엔드포인트에 연결하는 방법에 대한 자세한 내용은 [PowerShell Core의 WS-Management 원격 기능](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="00494-195">Windows PowerShell 원격 작업을 사용하려면 원격 관리를 위해 원격 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="00494-196">자세한 내용과 지침은 [원격 요구 사항 정보](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="00494-197">원격 기능을 이용한 작업에 대한 자세한 내용은 [원격 기능에 대한 정보](/powershell/module/microsoft.powershell.core/about/about_remote)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="00494-198">SSH 기반 원격 기능</span><span class="sxs-lookup"><span data-stu-id="00494-198">SSH-based remoting</span></span>

<span data-ttu-id="00494-199">**WinRM**과 같은 Windows 네이티브 구성 요소를 사용할 수 없는 다른 운영 체제를 지원하기 위해 PowerShell Core 6.x에 SSH 기반 원격 기능을 추가하였습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="00494-200">SSH 원격 기능은 대상 컴퓨터에 SSH 하위 시스템으로 PowerShell 호스트 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00494-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="00494-201">Windows 또는 Linux에서 SSH 기반 원격 기능을 설정하는 방법에 대한 자세한 내용과 예를 보려면 다음을 참조하세요. [SSH를 통한 PowerShell 원격 작업](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="00494-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="00494-202">PowerShell 갤러리(PSGallery)에는 SSH 기반 원격 기능을 자동으로 구성하는 모듈 및 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="00494-203">[PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0)에서 `Microsoft.PowerShell.RemotingTools` 모듈을 설치하고 `Enable-SSH` cmdlet을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="00494-204">`New-PSSession`, `Enter-PSSession` 및 `Invoke-Command` cmdlet에는 SSH 연결을 지원하는 새로운 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="00494-205">원격 세션을 만들려면 **HostName** 매개 변수를 사용하여 대상 컴퓨터를 지정하고 **UserName**을 사용하여 사용자 이름을 제공하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="00494-206">cmdlet을 대화형으로 실행하면 암호를 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="00494-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="00494-207">또는 **HostName** 매개 변수를 사용할 때 사용자 이름 정보를 제공하세요. 이 이름 다음에는 '\@' 기호와 컴퓨터 이름이 차례로 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="00494-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign ('@'), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="00494-208">**KeyFilePath** 매개 변수와 함께 프라이빗 키 파일을 사용하여 SSH 키 인증을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="00494-209">자세한 내용은 [OpenSSH 키 관리](/windows-server/administration/openssh/openssh_keymanagement)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="00494-210">지원되는 그룹 정책</span><span class="sxs-lookup"><span data-stu-id="00494-210">Group Policy supported</span></span>

<span data-ttu-id="00494-211">PowerShell에는 엔터프라이즈 환경에서 서버에 대해 일관된 옵션 값을 정의하는 데 도움이 되는 그룹 정책 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="00494-212">이러한 설정에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00494-212">These settings include:</span></span>

- <span data-ttu-id="00494-213">콘솔 세션 구성: PowerShell이 실행되는 구성 엔드포인트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="00494-214">모듈 로깅 켜기: 모듈의 LogPipelineExecutionDetails 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="00494-215">PowerShell 스크립트 블록 로깅 켜기: 모든 PowerShell 스크립트의 자세한 로깅을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="00494-216">스크립트 실행 켜기: PowerShell 실행 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="00494-217">PowerShell 기록 켜기: PowerShell 명령의 입력 및 출력을 텍스트 기반 기록으로 캡처하는 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="00494-218">Update-Help의 기본 원본 경로 설정: Updatable Help의 원본을 인터넷이 아닌 디렉터리로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="00494-219">자세한 내용은 [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="00494-220">PowerShell 7의 경우 `$PSHOME`에 그룹 정책 템플릿과 설치 스크립트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="00494-221">그룹 정책 도구에서는 관리 템플릿 파일(`.admx`, `.adml`)을 사용하여 사용자 인터페이스에 정책 설정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="00494-222">이를 통해 관리자는 레지스트리 기반 정책 설정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="00494-223">`InstallPSCorePolicyDefinitions.ps1` 스크립트를 통해 로컬 컴퓨터에 PowerShell Core 관리 템플릿이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="00494-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="00494-224">별도의 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="00494-224">Separate Event Logs</span></span>

<span data-ttu-id="00494-225">Windows PowerShell과 PowerShell 7은 별도의 이벤트 로그에 이벤트를 로그합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="00494-226">PowerShell 로그의 목록을 가져오려면 다음 명령을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="00494-227">자세한 내용은 [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="00494-228">Visual Studio Code로 향상된 편집 환경</span><span class="sxs-lookup"><span data-stu-id="00494-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="00494-229">[PowerShell 확장](https://code.visualstudio.com/docs/languages/powershell)이 포함된 [Visual Studio Code(VSCode)](https://code.visualstudio.com/)는 PowerShell 7에 대해 지원되는 스크립팅 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="00494-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="00494-230">Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="00494-231">업데이트된 PowerShell 확장은 다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="00494-232">새로운 ISE 호환 모드</span><span class="sxs-lookup"><span data-stu-id="00494-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="00494-233">구문 강조 표시, 여러 줄 편집, 역검색을 포함한 통합 콘솔의 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="00494-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="00494-234">안정성 및 성능 향상</span><span class="sxs-lookup"><span data-stu-id="00494-234">Stability and performance improvements</span></span>
- <span data-ttu-id="00494-235">새로운 CodeLens 통합</span><span class="sxs-lookup"><span data-stu-id="00494-235">New CodeLens integration</span></span>
- <span data-ttu-id="00494-236">향상된 경로 자동 완성 기능</span><span class="sxs-lookup"><span data-stu-id="00494-236">Improved path auto-completion</span></span>

<span data-ttu-id="00494-237">Visual Studio로 더 쉽게 전환하려면 **명령 팔레트**에서 제공하는 **ISE 모드 사용** 함수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="00494-238">이 함수를 통해 VSCode가 ISE 스타일 레이아웃으로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="00494-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="00494-239">ISE 스타일 레이아웃은 친숙한 사용자 환경에서 PowerShell의 모든 새로운 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00494-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="00494-240">새로운 ISE 레이아웃으로 전환하려면 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 눌러 **명령 팔레트**를 열고, `PowerShell`을 입력한 후 **PowerShell: ISE 모드 사용**을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="00494-241">레이아웃을 원본 레이아웃으로 설정하려면 **명령 팔레트**를 열고, **PowerShell: ISE 모드 사용 안 함(기본값으로 복원)** 을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="00494-242">ISE에 맞게 VSCode 레이아웃을 사용자 지정하는 방법에 대한 자세한 내용은 [Visual Studio Code에서 ISE 환경을 복제하는 방법](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00494-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="00494-243">ISE를 새 기능으로 업데이트할 계획이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="00494-244">이제 ISE 기능은 최신 버전의 Windows 10 및 Windows Server에서 사용자가 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="00494-245">ISE를 영구적으로 제거할 계획이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="00494-246">PowerShell 팀과 파트너는 Visual Studio Code에 대한 PowerShell 확장의 스크립팅 환경을 개선하는 데 집중하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00494-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="00494-247">다음 단계</span><span class="sxs-lookup"><span data-stu-id="00494-247">Next Steps</span></span>

<span data-ttu-id="00494-248">효율적으로 마이그레이션할 수 있는 지식을 갖추었으니 이제 [PowerShell 7를 설치](/powershell/scripting/install/installing-powershell-core-on-windows)해 보세요!</span><span class="sxs-lookup"><span data-stu-id="00494-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
