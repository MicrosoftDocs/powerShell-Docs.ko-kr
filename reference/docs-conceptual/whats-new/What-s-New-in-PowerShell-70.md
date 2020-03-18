---
title: PowerShell 7.0의 새로운 기능
description: PowerShell 7.0에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 03/04/2020
ms.openlocfilehash: 6915bb70d6e54da86d2b935e3feed8d7f3770ba9
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404989"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="cb44d-103">PowerShell 7.0의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="cb44d-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="cb44d-104">PowerShell 7.0은 서로 다른 환경 및 하이브리드 클라우드를 관리하도록 빌드된 오픈 소스 플랫폼 간 (Windows, macOS 및 Linux) 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="cb44d-105">이 릴리스에서는 다음과 같은 다양한 새로운 기능이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="cb44d-106">`ForEach-Object -Parallel`을 사용한 파이프라인 병렬 처리</span><span class="sxs-lookup"><span data-stu-id="cb44d-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="cb44d-107">새 연산자:</span><span class="sxs-lookup"><span data-stu-id="cb44d-107">New operators:</span></span>
  - <span data-ttu-id="cb44d-108">삼항 연산자: `a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="cb44d-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="cb44d-109">파이프라인 체인 연산자: `||` 및 `&&`</span><span class="sxs-lookup"><span data-stu-id="cb44d-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="cb44d-110">Null 조건 연산자: `??` 및 `??=`</span><span class="sxs-lookup"><span data-stu-id="cb44d-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="cb44d-111">오류 조사를 용이하게 하는 간소화된 동적 오류 보기 및 `Get-Error` cmdlet</span><span class="sxs-lookup"><span data-stu-id="cb44d-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="cb44d-112">사용자가 암시적 Windows PowerShell 세션에서 모듈을 가져올 수 있는 호환성 계층</span><span class="sxs-lookup"><span data-stu-id="cb44d-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="cb44d-113">자동 새 버전 알림</span><span class="sxs-lookup"><span data-stu-id="cb44d-113">Automatic new version notifications</span></span>
- <span data-ttu-id="cb44d-114">PowerShell 7에서 직접 DSC 리소스를 호출하는 기능(실험적)</span><span class="sxs-lookup"><span data-stu-id="cb44d-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="cb44d-115">기능 및 수정 사항의 전체 목록을 보려면 [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="cb44d-116">PowerShell은 어디에 설치할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="cb44d-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="cb44d-117">PowerShell 7은 현재 다음과 같은 x64 운영 체제를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="cb44d-118">Windows 8.1 및 10</span><span class="sxs-lookup"><span data-stu-id="cb44d-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="cb44d-119">Windows Server 2012, 2012 R2, 2016, 2019</span><span class="sxs-lookup"><span data-stu-id="cb44d-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="cb44d-120">macOS 10.13 이상 버전</span><span class="sxs-lookup"><span data-stu-id="cb44d-120">macOS 10.13+</span></span>
- <span data-ttu-id="cb44d-121">Red Hat Enterprise Linux(RHEL) / CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb44d-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="cb44d-122">Fedora 30 이상 버전</span><span class="sxs-lookup"><span data-stu-id="cb44d-122">Fedora 30+</span></span>
- <span data-ttu-id="cb44d-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb44d-123">Debian 9</span></span>
- <span data-ttu-id="cb44d-124">Ubuntu LTS 16.04 이상 버전</span><span class="sxs-lookup"><span data-stu-id="cb44d-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="cb44d-125">Alpine Linux 3.8 이상 버전</span><span class="sxs-lookup"><span data-stu-id="cb44d-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="cb44d-126">또한 PowerShell 7.0은 Debian, Ubuntu 및 ARM64 Alpine Linux의 ARM32 및 ARM64 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="cb44d-127">기본 운영 체제 [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) 또는 [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7)에 대한 설치 지침을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="cb44d-128">공식적으로 지원되는 것은 아니지만 커뮤니티는 [Arch](https://aur.archlinux.org/packages/powershell/) 및 Kali Linux에 대한 패키지도 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-129">Debian 10 및 CentOS 8은 현재 WinRM 원격을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="cb44d-130">SSH 기반 원격을 설정하는 방법에 대한 자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="cb44d-131">지원되는 운영 체제 및 지원 주기에 대한 최신 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="cb44d-132">PowerShell 7 실행</span><span class="sxs-lookup"><span data-stu-id="cb44d-132">Running PowerShell 7</span></span>

<span data-ttu-id="cb44d-133">PowerShell 7은 새 디렉터리에 설치되고 Windows PowerShell 5.1과 나란히 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-133">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="cb44d-134">PowerShell Core 6.x의 경우 PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-134">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="cb44d-135">PowerShell 7은 `%programfiles%\PowerShell\7`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-135">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="cb44d-136">`%programfiles%\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-136">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="cb44d-137">PowerShell 7 설치 관리자 패키지는 이전 버전의 PowerShell Core 6.x를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-137">The PowerShell 7 installer packages upgrade previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="cb44d-138">Windows의 PowerShell Core 6.x: `%programfiles%\PowerShell\6`이 `%programfiles%\PowerShell\7`로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-138">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="cb44d-139">Linux: `/opt/microsoft/powershell/6`이 `/opt/microsoft/powershell/7`로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-139">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="cb44d-140">macOS: `/usr/local/microsoft/powershell/6`이 `/usr/local/microsoft/powershell/7`로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-140">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-141">Windows PowerShell에서 PowerShell을 시작하는 실행 파일의 이름은 `powershell.exe`입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-141">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="cb44d-142">버전 6 이상에서는 실행 파일이 병렬 실행을 지원하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-142">In version 6 and above, the executable is changed to support side-by-side execution.</span></span> <span data-ttu-id="cb44d-143">PowerShell 7을 시작하는 새 실행 파일은 `pwsh.exe`입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-143">The new executable to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="cb44d-144">미리 보기 빌드는 7-preview 디렉터리 아래에 `pwsh` 대신 `pwsh-preview`로 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-144">Preview builds will remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="cb44d-145">Windows PowerShell과의 이전 버전 호환성 개선</span><span class="sxs-lookup"><span data-stu-id="cb44d-145">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="cb44d-146">PowerShell 7.0은 .NET Core 3.1로 전환하여 기존 Windows PowerShell 모듈과 훨씬 향상된 이전 버전 호환성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-146">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="cb44d-147">여기에는 Windows의 일부로 제공되는 다양한 역할 관리 모듈뿐만 아니라 Windows에서 `Out-GridView` 및 `Show-Command` 같은 GUI 기능이 필요한 많은 모듈이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-147">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="cb44d-148">Windows의 경우 새 스위치 매개 변수 **UseWindowsPowerShell**이 `Import-Module`에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-148">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="cb44d-149">이 스위치는 로컬 Windows PowerShell 프로세스를 사용하여 해당 모듈에 포함된 모든 cmdlet을 암시적으로 실행하는 PowerShell 7의 프록시 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-149">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="cb44d-150">자세한 내용은 [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-150">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="cb44d-151">Microsoft 모듈에서 PowerShell 7.0을 사용하는 방법에 대한 자세한 내용은 [모듈 호환성 표](https://aka.ms/PSModuleCompat)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-151">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="cb44d-152">ForEach-Object에 병렬 실행 추가</span><span class="sxs-lookup"><span data-stu-id="cb44d-152">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="cb44d-153">컬렉션의 항목을 반복하는 `ForEach-Object` cmdlet은 이제 새로운 **Parallel** 매개 변수를 사용하여 병렬 처리를 기본 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-153">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="cb44d-154">기본적으로 병렬 스크립트 블록은 병렬 작업을 시작한 호출자의 현재 작업 디렉터리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-154">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="cb44d-155">다음 예제에서는 로컬 Windows 컴퓨터에 있는 5개의 시스템 로그에서 5만 개의 로그 항목을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-155">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="cb44d-156">**Parallel** 매개 변수는 각 입력 로그 이름에 대해 병렬로 실행되는 스크립트 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-156">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="cb44d-157">새로운 **ThrottleLimit** 매개 변수는 지정된 시간에 동시에 실행되는 스크립트 블록 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-157">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="cb44d-158">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-158">The default is 5.</span></span>

<span data-ttu-id="cb44d-159">`$_` 변수를 사용하여 스크립트 블록 내의 현재 입력 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-159">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="cb44d-160">`$using:` 범위를 사용하여 실행 중인 스크립트 블록에 변수 참조를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-160">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="cb44d-161">자세한 내용은 [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-161">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="cb44d-162">삼항 연산자</span><span class="sxs-lookup"><span data-stu-id="cb44d-162">Ternary operator</span></span>

<span data-ttu-id="cb44d-163">PowerShell 7.0에는 단순화된 `if-else` 문처럼 동작하는 삼항 연산자가 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-163">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="cb44d-164">PowerShell의 삼항 연산자는 C# 삼항 연산자 구문에서 유사하게 모델링됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-164">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="cb44d-165">조건 식이 항상 평가되고 그 결과가 **부울**로 변환되어 다음에 평가되는 분기를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-165">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="cb44d-166">`<condition>` 식이 true인 경우 `<if-true>` 식이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-166">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="cb44d-167">`<condition>` 식이 false인 경우 `<if-false>` 식이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-167">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="cb44d-168">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-168">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="cb44d-169">이 예제에서는 경로가 존재하는 경우 **Path exists**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-169">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="cb44d-170">경로가 존재하지 않는 경우 **Path not found**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-170">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="cb44d-171">자세한 내용은 [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-171">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="cb44d-172">파이프라인 체인 연산자</span><span class="sxs-lookup"><span data-stu-id="cb44d-172">Pipeline chain operators</span></span>

<span data-ttu-id="cb44d-173">PowerShell 7은 `&&` 및 `||` 연산자를 구현하여 조건부로 파이프라인을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-173">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="cb44d-174">이러한 연산자는 PowerShell에서 "파이프라인 체인 연산자"로 알려져 있으며 **Bash** 및 **Zsh**와 같은 셸에서 AND 및 OR 목록과 비슷하고 Windows 명령 셸(**cmd.exe**)에서 조건 처리 기호와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-174">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="cb44d-175">`&&` 연산자는 왼쪽 파이프라인이 성공한 경우 오른쪽 파이프라인을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-175">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="cb44d-176">반대로, `||` 연산자는 왼쪽 파이프라인이 실패한 경우 오른쪽 파이프라인을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-176">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-177">이러한 연산자는 `$?` 및 `$LASTEXITCODE` 변수를 사용하여 파이프라인이 실패했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-177">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="cb44d-178">이렇게 하면 cmdlet 또는 함수뿐만 아니라 네이티브 명령과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-178">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="cb44d-179">여기서는 첫 번째 명령이 성공하고 두 번째 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-179">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="cb44d-180">여기서는 첫 번째 명령이 실패하고 두 번째 명령이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-180">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="cb44d-181">여기서는 첫 번째 명령이 성공하고 두 번째 명령이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-181">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="cb44d-182">여기서는 첫 번째 명령이 실패했으므로 두 번째 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-182">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="cb44d-183">자세한 내용은 [파이프라인 체인 연산자](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-183">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="cb44d-184">Null 병합, 할당 및 조건 연산자</span><span class="sxs-lookup"><span data-stu-id="cb44d-184">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="cb44d-185">PowerShell 7에는 Null 병합 연산자 `??`, Null 조건 할당 `??=`, Null 조건 멤버 액세스 연산자 `?.` 및 `?[]`가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-185">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="cb44d-186">Null 병합 연산자 ??</span><span class="sxs-lookup"><span data-stu-id="cb44d-186">Null-coalescing Operator ??</span></span>

<span data-ttu-id="cb44d-187">Null 병합 연산자 `??`는 null이 아닌 경우 왼쪽 피연산자의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-187">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="cb44d-188">그렇지 않으면 오른쪽 피연산자를 계산하고 그 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-188">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="cb44d-189">`??` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-189">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="cb44d-190">다음 예제에서는 오른쪽 피연산자가 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-190">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="cb44d-191">Null 조건 할당 연산자 ??=</span><span class="sxs-lookup"><span data-stu-id="cb44d-191">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="cb44d-192">Null 조건 할당 연산자 `??=`는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우에만 오른쪽 피연산자의 값을 왼쪽 피연산자에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-192">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="cb44d-193">`??=` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-193">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="cb44d-194">다음 예제에서는 오른쪽 피연산자가 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-194">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="cb44d-195">Null 조건 멤버 액세스 ?.</span><span class="sxs-lookup"><span data-stu-id="cb44d-195">Null conditional member access operators ?.</span></span> <span data-ttu-id="cb44d-196">및 ?[](실험적)</span><span class="sxs-lookup"><span data-stu-id="cb44d-196">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-197">**PSNullConditionalOperators**라는 실험적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-197">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="cb44d-198">자세한 내용은 [실험적 기능](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-198">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="cb44d-199">Null 조건 연산자는 해당 피연산자가 null이 아닌 것으로 평가되는 경우에만 멤버 액세스 `?.` 또는 요소 액세스 `?[]`를 해당 피연산자로 사용할 수 있습니다. 그렇지 않으면 null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-199">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-200">PowerShell을 사용하면 `?`를 변수 이름에 포함할 수 있으므로 이러한 연산자를 사용하려면 변수 이름의 공식적인 사양이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-200">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="cb44d-201">따라서 `{}`를 `${a}`와 같이 변수 이름 주위에 사용하거나 `?`이 변수 이름의 일부인 경우(`${a?}`)에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-201">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="cb44d-202">다음 예제에서는 멤버 속성 **Status**의 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-202">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="cb44d-203">다음 예제에서는 멤버 이름 **Status**에 액세스하지 않고 null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-203">The following example will return null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="cb44d-204">마찬가지로 `?[]`를 사용하여 요소 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-204">Similarly, using `?[]`, the value of the element will be returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="cb44d-205">피연산자가 null이면 요소에 액세스하지 않고 null이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-205">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="cb44d-206">자세한 내용은 [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-206">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="cb44d-207">새로운 보기 ConciseView 및 cmdlet Get-Error</span><span class="sxs-lookup"><span data-stu-id="cb44d-207">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="cb44d-208">새로운 기본 보기 **ConciseView**를 사용하여 대화형 및 스크립트 오류를 쉽게 읽을 수 있도록 오류 메시지의 표시 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-208">The display of error messages has been improved to enhance the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="cb44d-209">보기는 기본 설정 변수 `$ErrorView`를 통해 사용자가 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-209">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="cb44d-210">**ConciseView**를 사용하는 경우, 오류가 스크립트 또는 파서에서 발생하지 않은 한 다음과 같은 한 줄 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-210">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="cb44d-211">스크립트를 실행하는 동안 오류가 발생하거나 구문 분석 오류가 발생하는 경우, PowerShell은 오류, 포인터 및 해당 줄에서 오류 위치를 표시하는 오류 메시지를 포함하는 여러 줄 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-211">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="cb44d-212">터미널이 ANSI 색 이스케이프 시퀀스(VT100)을 지원하지 않는 경우 색은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-212">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![스크립트의 오류 표시](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="cb44d-214">PowerShell 7의 기본 보기는 **ConciseView**입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-214">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="cb44d-215">이전의 기본 보기는 **NormalView**였으며 기본 설정 변수 `$ErrorView`를 설정하여 사용자가 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-215">The previous default view was **NormalView** and is user selectable by setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="cb44d-216">새로운 속성 **ErrorAccentColor**가 `$Host.PrivateData`에 추가되어 오류 메시지의 강조 색 변경을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-216">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="cb44d-217">새로운 cmdlet `Get-Error`는 원하는 경우 정규화된 오류에 대한 전체 세부 보기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-217">A new cmdlet `Get-Error` provides complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="cb44d-218">기본적으로 이 cmdlet은 발생한 마지막 오류의 내부 예외를 비롯한 전체 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-218">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Get-Error의 표시](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="cb44d-220">`Get-Error` cmdlet은 기본 제공 변수 `$Error`를 사용하여 파이프라인으로부터 입력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-220">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="cb44d-221">`Get-Error`는 파이핑되는 오류를 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-221">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="cb44d-222">`Get-Error` cmdlet은 **Newest** 매개 변수를 지원하므로 현재 세션에서 표시하려는 오류 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-222">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="cb44d-223">자세한 내용은 [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-223">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="cb44d-224">새 버전 알림</span><span class="sxs-lookup"><span data-stu-id="cb44d-224">New version notification</span></span>

<span data-ttu-id="cb44d-225">PowerShell 7은 업데이트 알림을 사용하여 PowerShell 업데이트가 있음을 사용자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-225">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="cb44d-226">PowerShell은 하루 한 번 온라인 서비스를 쿼리하여 최신 버전을 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-226">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-227">업데이트 확인은 지정된 24시간 동안 첫 번째 세션 중에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-227">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="cb44d-228">성능상의 이유로 업데이트 확인은 세션 시작 3초 후에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-228">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="cb44d-229">알림은 후속 세션이 시작될 때만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-229">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="cb44d-230">기본적으로 PowerShell은 버전/분기에 따라 두 가지 알림 채널 중 하나를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-230">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="cb44d-231">지원되는 GA(일반 공급) 버전의 PowerShell은 업데이트된 GA 릴리스에 대한 알림만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-231">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="cb44d-232">미리 보기 및 RC(릴리스 후보) 릴리스는 미리 보기, RC 및 GA 릴리스에 대한 업데이트 알림을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-232">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="cb44d-233">업데이트 알림 동작은 `$Env:POWERSHELL_UPDATECHECK` 환경 변수를 사용하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-233">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="cb44d-234">지원되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-234">The following values are supported:</span></span>

- <span data-ttu-id="cb44d-235">**Default**는 `$Env:POWERSHELL_UPDATECHECK`을 정의 하지 않는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-235">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="cb44d-236">GA 릴리스는 GA 릴리스 업데이트를 알림</span><span class="sxs-lookup"><span data-stu-id="cb44d-236">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="cb44d-237">미리 보기/RC 릴리스는 GA 및 미리 보기 릴리스 업데이트를 알림</span><span class="sxs-lookup"><span data-stu-id="cb44d-237">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="cb44d-238">**Off**는 업데이트 알림 기능을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-238">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="cb44d-239">**LTS**는 LTS(장기 서비스) GA 릴리스 업데이트만 알립니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-239">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-240">환경 변수 `$Env:POWERSHELL_UPDATECHECK`는 처음으로 설정될 때까지 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-240">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="cb44d-241">`LTS` 릴리스만 버전 알림을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cb44d-241">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="cb44d-242">버전 알림을 `Default` 동작으로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cb44d-242">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="cb44d-243">자세한 내용은 [업데이트 알림](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-243">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="cb44d-244">Invoke-DSCResource를 사용한 새로운 DSC 리소스 지원(실험적)</span><span class="sxs-lookup"><span data-stu-id="cb44d-244">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="cb44d-245">**PSDesiredStateConfiguration.InvokeDscResource**라는 실험적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-245">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="cb44d-246">자세한 내용은 [실험적 기능](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-246">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="cb44d-247">`Invoke-DscResource` cmdlet은 지정된 PowerShell DSC(Desired State Configuration) 리소스의 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-247">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="cb44d-248">이 cmdlet은 구성 문서를 만들지 않고 DSC 리소스를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-248">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="cb44d-249">이 cmdlet을 사용하면 구성 관리 제품이 DSC 리소스를 사용하여 Windows 또는 Linux를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-249">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="cb44d-250">이 cmdlet을 사용하면 디버깅을 사용하도록 설정한 상태에서 DSC 엔진이 실행 중일 때에도 리소스를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-250">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="cb44d-251">이 명령은 Log라는 리소스의 **Set** 메서드를 호출하고 **Message** 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44d-251">This command invokes the **Set** method of a resource named Log and specifies a **Message** property.</span></span>

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

<span data-ttu-id="cb44d-252">자세한 내용은 [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb44d-252">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="cb44d-253">주요 변경 내용 및 개선 사항</span><span class="sxs-lookup"><span data-stu-id="cb44d-253">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="cb44d-254">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="cb44d-254">Breaking Changes</span></span>

- <span data-ttu-id="cb44d-255">업데이트 알림이 LTS 및 기본 채널을 지원(#11132)</span><span class="sxs-lookup"><span data-stu-id="cb44d-255">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="cb44d-256">Windows PowerShell에서와 같은 방식으로 작동하도록 Test-Connection을 업데이트(#10697)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-256">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-257">Preserve $? -</span><span class="sxs-lookup"><span data-stu-id="cb44d-257">Preserve $?</span></span> <span data-ttu-id="cb44d-258">ParenExpression, SubExpression 및 ArrayExpression(#11040)</span><span class="sxs-lookup"><span data-stu-id="cb44d-258">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="cb44d-259">Start-Job에서 작업 디렉터리를 현재 디렉터리로 설정(#10920)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-259">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-260">세션 내 문화권 변경에서 $PSCulture를 일관되게 반영(#10138)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-260">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="cb44d-261">엔진 업데이트 및 수정</span><span class="sxs-lookup"><span data-stu-id="cb44d-261">Engine Updates and Fixes</span></span>

- <span data-ttu-id="cb44d-262">원격 시나리오용 중단점 API 기능을 향상(#11312)</span><span class="sxs-lookup"><span data-stu-id="cb44d-262">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="cb44d-263">다른 Runspace로 누수되는 PowerShell 클래스 정의를 수정(#11273)</span><span class="sxs-lookup"><span data-stu-id="cb44d-263">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="cb44d-264">7\.0.0-Preview1에 추가된 FirstOrDefault 기본 형식으로 인한 서식 지정 재발 문제를 수정(#11258)</span><span class="sxs-lookup"><span data-stu-id="cb44d-264">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="cb44d-265">PS7 원격 분석에서 추적할 Microsoft 모듈을 추가(#10751)</span><span class="sxs-lookup"><span data-stu-id="cb44d-265">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="cb44d-266">승인된 기능을 비 실험적으로 설정(#11303)</span><span class="sxs-lookup"><span data-stu-id="cb44d-266">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="cb44d-267">해당하는 경우 TargetObject를 사용하도록 ConciseView를 업데이트(#11075)</span><span class="sxs-lookup"><span data-stu-id="cb44d-267">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="cb44d-268">CompletionCompleters 공용 메서드에서 NullReferenceException을 수정(#11274)</span><span class="sxs-lookup"><span data-stu-id="cb44d-268">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="cb44d-269">비 Windows 플랫폼에 대한 아파트 스레드 상태 검사를 수정(#11301)</span><span class="sxs-lookup"><span data-stu-id="cb44d-269">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="cb44d-270">프로세스 및 컴퓨터 환경 변수를 연결하는 PSModulePath 설정을 업데이트(#11276)</span><span class="sxs-lookup"><span data-stu-id="cb44d-270">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="cb44d-271">.NET Core를 3.1.0으로 변경(#11260)</span><span class="sxs-lookup"><span data-stu-id="cb44d-271">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="cb44d-272">$env:PATH 앞에서 $PSHOME 검색을 수정(#11141)</span><span class="sxs-lookup"><span data-stu-id="cb44d-272">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="cb44d-273">pwsh가 $env:PSModulePath를 상속하고 powershell.exe를 올바르게 시작하도록 설정(#11057)</span><span class="sxs-lookup"><span data-stu-id="cb44d-273">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="cb44d-274">.NET Core 3.1 미리 보기 1로 이동(#10798)</span><span class="sxs-lookup"><span data-stu-id="cb44d-274">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="cb44d-275">파일 시스템 공급자에서 재분석 태그 검사를 리팩터링(#10431)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-275">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-276">스크립트 로깅에서 CR 및 새 줄을 0x23CE 문자로 바꿈(#10616)</span><span class="sxs-lookup"><span data-stu-id="cb44d-276">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="cb44d-277">AppDomain.CurrentDomain.ProcessExit에서 이벤트 처리기를 등록 취소하여 리소스 누수 문제를 수정(#10626)</span><span class="sxs-lookup"><span data-stu-id="cb44d-277">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="cb44d-278">디버그, 오류, 정보, 진행률, 자세한 정보 표시 또는 경고 메시지가 생성될 때 디버거로 중단되도록 ActionPreference.Break 지원을 추가(#8205)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-278">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-279">.CPL 확장명을 지정하지 않고 PowerShell Core 내에서 제어판 추가 기능을 시작하도록 허용</span><span class="sxs-lookup"><span data-stu-id="cb44d-279">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="cb44d-280">(#9828)</span><span class="sxs-lookup"><span data-stu-id="cb44d-280">(#9828)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="cb44d-281">일반 Cmdlet 업데이트 및 수정</span><span class="sxs-lookup"><span data-stu-id="cb44d-281">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="cb44d-282">UnixStat 실험적 기능에서 파일 변경 날짜를 설정하기 위해 Raspbian 문제를 수정(#11313)</span><span class="sxs-lookup"><span data-stu-id="cb44d-282">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="cb44d-283">ConvertFrom-SecureString에 -AsPlainText를 추가(#11142)</span><span class="sxs-lookup"><span data-stu-id="cb44d-283">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="cb44d-284">WinCompat에 대한 WindowsPS 버전 검사를 추가(#11148)</span><span class="sxs-lookup"><span data-stu-id="cb44d-284">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="cb44d-285">일부 WinCompat 시나리오에서 오류 보고를 수정(#11259)</span><span class="sxs-lookup"><span data-stu-id="cb44d-285">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="cb44d-286">네이티브 이진 해결 프로그램 추가(#11032)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-286">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-287">CJK 문자를 올바르게 적용하도록 문자 너비 계산을 업데이트(#11262)</span><span class="sxs-lookup"><span data-stu-id="cb44d-287">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="cb44d-288">macOS에 대한 Unblock-File 추가(#11137)</span><span class="sxs-lookup"><span data-stu-id="cb44d-288">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="cb44d-289">Get-PSCallStack에서 재발 문제를 수정(#11210)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-289">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-290">Job cmdlet을 사용할 때 ScheduledJob 모듈 자동 로딩을 제거(#11194)</span><span class="sxs-lookup"><span data-stu-id="cb44d-290">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="cb44d-291">Get-Error cmdlet에 OutputType을 추가하고 기존 typenames를 유지(#10856)</span><span class="sxs-lookup"><span data-stu-id="cb44d-291">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="cb44d-292">SupportsVirtualTerminal 속성에서 null 참조를 수정(#11105)</span><span class="sxs-lookup"><span data-stu-id="cb44d-292">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="cb44d-293">Get-WinEvent에서 제한 확인을 추가(#10648)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-293">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-294">StopUpstreamCommandsException 변수가 채워지지 않도록 명령 런타임을 수정(#10840)</span><span class="sxs-lookup"><span data-stu-id="cb44d-294">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="cb44d-295">네이티브 명령에 대해 출력 인코딩을 [Console]::OutputEncoding으로 설정(#10824)</span><span class="sxs-lookup"><span data-stu-id="cb44d-295">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="cb44d-296">예제에서 여러 줄 코드 블록을 지원(#10776)(@Greg-Smulko에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-296">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="cb44d-297">Select-String cmdlet에 Culture 매개 변수를 추가(#10943)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-297">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-298">후행 백슬래시를 포함하는 Start-Job 작업 디렉터리를 수정(#11041)</span><span class="sxs-lookup"><span data-stu-id="cb44d-298">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="cb44d-299">ConvertFrom-Json: 기본적으로 컬렉션을 래핑 해제(#10861)(@danstur에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-299">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="cb44d-300">-CaseSensitive 및-AsHashtable 스위치를 사용하여 Group-Object cmdlet용 해시 테이블에서 대/소문자 구분(#11030)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-300">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-301">올바른 대/소문자를 가지도록 경로를 다시 작성할 때 파일을 열거할 수 없으면 예외 처리(#11014)</span><span class="sxs-lookup"><span data-stu-id="cb44d-301">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="cb44d-302">myCommand 대신 작업을 표시하도록 ConciseView를 수정(#11007)</span><span class="sxs-lookup"><span data-stu-id="cb44d-302">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="cb44d-303">웹 cmdlet이 HTTP 오류 상태를 무시하도록 허용(#10466)(@vdamewood에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-303">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="cb44d-304">Get-Command에 대한 둘 이상의 CommandInfo 파이핑을 수정(#10929).</span><span class="sxs-lookup"><span data-stu-id="cb44d-304">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="cb44d-305">Windows용 Get-Counter cmdlet 추가(#10933)</span><span class="sxs-lookup"><span data-stu-id="cb44d-305">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="cb44d-306">ConvertTo-Json이 [AutomationNull]::Value 및 [NullString]::Value를 $null로 처리하도록 설정(#10957)</span><span class="sxs-lookup"><span data-stu-id="cb44d-306">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="cb44d-307">SSH 원격에 대한 ipv6 주소에서 대괄호 제거(#10968)</span><span class="sxs-lookup"><span data-stu-id="cb44d-307">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="cb44d-308">pwsh에 보낸 명령이 공백만 있는 경우 충돌 해결(#10977)</span><span class="sxs-lookup"><span data-stu-id="cb44d-308">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="cb44d-309">플랫폼 간 Get-Clipboard 및 Set-Clipboard 추가(#10340)</span><span class="sxs-lookup"><span data-stu-id="cb44d-309">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="cb44d-310">파일 시스템 개체의 원래 경로 설정을 불필요한 후행 슬래시를 포함하지 않도록 수정(#10959)</span><span class="sxs-lookup"><span data-stu-id="cb44d-310">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="cb44d-311">ConvertTo-Json에 $null을 지원(#10947)</span><span class="sxs-lookup"><span data-stu-id="cb44d-311">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="cb44d-312">Windows에 Out-Printer 명령을 다시 추가(#10906)</span><span class="sxs-lookup"><span data-stu-id="cb44d-312">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="cb44d-313">공백을 포함하는 Start-Job -WorkingDirectory를 수정(#10951)</span><span class="sxs-lookup"><span data-stu-id="cb44d-313">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="cb44d-314">PSConfiguration.cs 설정에 Null을 가져올 때 기본 값을 반환(#10963)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-314">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-315">IO 예외를 종료되지 않는 것으로 처리(#10950)</span><span class="sxs-lookup"><span data-stu-id="cb44d-315">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="cb44d-316">GraphicalHost 어셈블리를 추가하여 Out-GridView, Show-Command 및 Get-Help -ShowWindow를 사용(#10899)</span><span class="sxs-lookup"><span data-stu-id="cb44d-316">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="cb44d-317">Get-HotFix에서 파이프라인을 통해 ComputerName을 가져옴(#10852)(@kvprasoon에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-317">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="cb44d-318">일반 매개 변수를 사용 가능한 것으로 표시하도록 매개 변수에 대한 탭 완성을 수정(#10850)</span><span class="sxs-lookup"><span data-stu-id="cb44d-318">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="cb44d-319">GetCorrectCasedPath()을 수정하여 First()를 호출하기 전에 시스템 파일 항목이 반환되는지 먼저 확인(#10930)</span><span class="sxs-lookup"><span data-stu-id="cb44d-319">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="cb44d-320">Start-Job에서 작업 디렉터리를 현재 디렉터리로 설정(#10920)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-320">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-321">TabExpansion2를 -CursorColumn을 요구하지 않고 $InputScript.Length로 처리하도록 변경(#10849)</span><span class="sxs-lookup"><span data-stu-id="cb44d-321">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="cb44d-322">호스트가 화면의 행 또는 열을 반환하지 않을 수 있는 경우를 처리(#10938)</span><span class="sxs-lookup"><span data-stu-id="cb44d-322">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="cb44d-323">강조 색을 지원하지 않는 호스트에서 강조 색 사용을 수정(#10937)</span><span class="sxs-lookup"><span data-stu-id="cb44d-323">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="cb44d-324">Update-List 명령을 다시 추가(#10922)</span><span class="sxs-lookup"><span data-stu-id="cb44d-324">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="cb44d-325">Clear-RecycleBin의 FWLink ID를 업데이트(#10925)</span><span class="sxs-lookup"><span data-stu-id="cb44d-325">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="cb44d-326">탭 완성 도중 파일 특성을 읽을 수 없는 경우 파일 건너뛰기(#10910)</span><span class="sxs-lookup"><span data-stu-id="cb44d-326">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="cb44d-327">Windows에서 Clear-RecycleBin을 다시 추가(#10909)</span><span class="sxs-lookup"><span data-stu-id="cb44d-327">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="cb44d-328">출력에 VT 이스케이프 시퀀스를 포함할지 여부를 제어하는 `$env:__SuppressAnsiEscapeSequences`를 추가(#10814)</span><span class="sxs-lookup"><span data-stu-id="cb44d-328">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="cb44d-329">-NoEmphasize 매개 변수를 추가하여 Select-String 출력을 색으로 구분(#8963)(@derek-xia에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-329">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="cb44d-330">Get-HotFix cmdlet을 다시 추가(#10740)</span><span class="sxs-lookup"><span data-stu-id="cb44d-330">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="cb44d-331">PowerShell을 호스트하는 애플리케이션에서 Add-Type을 사용할 수 있도록 설정(#10587)</span><span class="sxs-lookup"><span data-stu-id="cb44d-331">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="cb44d-332">LanguagePrimitives.IsNullLike()에서 보다 효과적인 평가 순서를 사용(#10781)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-332">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-333">Format-Hex에서 복합 컬렉션 파이프된 입력과 입력의 파이프된 스트림의 처리를 향상(#8674)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-333">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-334">SSHConnection 해시 테이블에서 값이 필요한 형식과 일치하지 않는 경우 형식 변환을 사용(#10720)(@SeeminglyScience에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-334">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="cb44d-335">-TotalCount가 설정된 경우 Get-Content -ReadCount 0 동작을 수정(#10749)(@eugenesmlv에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-335">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="cb44d-336">Get-WinEvent에서 액세스 거부 오류 메시지를 수정(#10639)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-336">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-337">열거형 또는 형식 제약된 변수 할당에 탭 완성을 사용(#10646)</span><span class="sxs-lookup"><span data-stu-id="cb44d-337">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="cb44d-338">서식 지정 문제를 일으키는 사용하지 않는 SourceLength 원격 속성을 제거(#10765)</span><span class="sxs-lookup"><span data-stu-id="cb44d-338">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="cb44d-339">ConvertFrom-StringData에 -Delimiter 매개 변수를 추가(#10665)(@steviecoaster에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-339">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="cb44d-340">SSH에서 Invoke-Command를 사용하는 경우 ScriptBlock에 대한 위치 매개 변수를 추가(#10721)(@machgo에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-340">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="cb44d-341">여러 줄이지만 ConciseView에 대한 스크립트 이름이 없는 경우 줄 컨텍스트 정보를 표시(#10746)</span><span class="sxs-lookup"><span data-stu-id="cb44d-341">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="cb44d-342">파일 시스템 공급자에 대한 \\wsl$\ 경로 지원을 추가(#10674)</span><span class="sxs-lookup"><span data-stu-id="cb44d-342">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="cb44d-343">파서에서 누락된 TokenKind.QuestionMark용 토큰 텍스트를 추가(#10706)</span><span class="sxs-lookup"><span data-stu-id="cb44d-343">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="cb44d-344">각 ForEach-Object -Parallel 실행 스크립트의 현재 작업 디렉터리를 호출하는 스크립트와 동일한 위치로 설정</span><span class="sxs-lookup"><span data-stu-id="cb44d-344">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="cb44d-345">(#10672)</span><span class="sxs-lookup"><span data-stu-id="cb44d-345">(#10672)</span></span>
- <span data-ttu-id="cb44d-346">FindFirstStreamW 및 FindNextStreamW API에 대해 api-ms-win-core-file-l1-2-2.dll을 Kernell32.dll로 바꿈(#10680)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-346">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-347">StrictMode를 더 허용하도록 도움말 서식 스크립트를 조정(#10563)</span><span class="sxs-lookup"><span data-stu-id="cb44d-347">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="cb44d-348">New-Service에 SecurityDescriptorSDDL 매개 변수를 추가(#10483)(@kvprasoon에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-348">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="cb44d-349">Test-Connection에서 정보 출력을 제거하고 ping 사용을 통합(#10478)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-349">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-350">액세스하지 않고 특수 재분석 지점 읽기(#10662)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-350">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-351">Clear-Host 출력을 터미널로 디렉션(#10681)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-351">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-352">Format-Table 및 -Property를 사용하여 그룹화를 위한 줄 바꿈을 다시 추가(#10653)</span><span class="sxs-lookup"><span data-stu-id="cb44d-352">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="cb44d-353">Get-Random의 -InputObject에서 [ValidateNotNullOrEmpty]를 제거하여 빈 문자열을 허용(#10644)</span><span class="sxs-lookup"><span data-stu-id="cb44d-353">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="cb44d-354">제안 시스템 문자열 간격 알고리즘에서 대/소문자를 구분 안 함(#10549)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-354">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-355">ForEach-Object -Parallel 입력 처리에서 null 참조 예외를 수정(#10577)</span><span class="sxs-lookup"><span data-stu-id="cb44d-355">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="cb44d-356">PowerShell Core 그룹 정책 정의를 추가(#10468)</span><span class="sxs-lookup"><span data-stu-id="cb44d-356">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="cb44d-357">Composability 시나리오에서 사용되는 XTPUSHSGR/XTPOPSGR VT 컨트롤 시퀀스를 지원하도록 콘솔 호스트를 업데이트</span><span class="sxs-lookup"><span data-stu-id="cb44d-357">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="cb44d-358">(#10208)</span><span class="sxs-lookup"><span data-stu-id="cb44d-358">(#10208)</span></span>
- <span data-ttu-id="cb44d-359">Start-Job에 WorkingDirectory 매개 변수를 추가(#10324)(@davinci26에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-359">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="cb44d-360">중단점 변경 내용을 호스트 runspace 디버거로 잘못 복제하는 이벤트 처리기를 제거(#10503)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-360">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-361">Microsoft.PowerShell.Commands.NativeMethods P/Invoke API에서 api-ms-win-core-job-12-1-0.dll을 Kernell32.dll로 바꿈(#10417)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-361">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-362">변수 할당 및 -OutVariable에서 New-Service에 대한 잘못된 출력을 수정(#10444)(@kvprasoon에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-362">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="cb44d-363">공백을 포함하는 종료 코드, 명령줄 매개 변수 및 경로와 관련된 전역 도구 문제를 해결(#10461)</span><span class="sxs-lookup"><span data-stu-id="cb44d-363">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="cb44d-364">OneDrive로 재귀를 수정 - SafeFindHandle 형식을 사용하도록 FindFirstFileEx()를 변경(#10405)</span><span class="sxs-lookup"><span data-stu-id="cb44d-364">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="cb44d-365">NVDA 화면 판독기가 활성 상태일 때 Windows에서 PSReadLine 자동 로드 건너뛰기(#10385)</span><span class="sxs-lookup"><span data-stu-id="cb44d-365">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="cb44d-366">7\.0.0.0에 대한 기본 제공 PowerShell 모듈 버전을 확대(#10356)</span><span class="sxs-lookup"><span data-stu-id="cb44d-366">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="cb44d-367">Add-Type에서 이름이 같은 형식이 이미 있을 경우 오류 throw를 추가(#9609)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-367">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="cb44d-368">성능</span><span class="sxs-lookup"><span data-stu-id="cb44d-368">Performance</span></span>

- <span data-ttu-id="cb44d-369">Parser.SaveError애서 closure 사용을 금지(#11006)</span><span class="sxs-lookup"><span data-stu-id="cb44d-369">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="cb44d-370">새 Regex 인스턴스를 만들 때 캐싱을 향상(#10657)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-370">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-371">types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml에서 PowerShell 기본 제공 형식 데이터 처리를 향상(#10898)</span><span class="sxs-lookup"><span data-stu-id="cb44d-371">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="cb44d-372">PSConfiguration.ReadValueFromFile을 더 빠르고 더 메모리 효율적으로 업데이트(#10839)</span><span class="sxs-lookup"><span data-stu-id="cb44d-372">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="cb44d-373">runspace 초기화를 위해 약간의 성능 개선을 추가(#10569)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-373">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-374">일반적으로 사용되는 시나리오에서 ForEach-Object 속도를 개선하고(#10454) 많은 runspace에서 ForEach-Object -Parallel 성능 문제를 수정(#10455)</span><span class="sxs-lookup"><span data-stu-id="cb44d-374">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="cb44d-375">코드 정리</span><span class="sxs-lookup"><span data-stu-id="cb44d-375">Code Cleanup</span></span>

- <span data-ttu-id="cb44d-376">Microsoft 표준에 맞게 주석 및 요소 텍스트를 변경(#11304)</span><span class="sxs-lookup"><span data-stu-id="cb44d-376">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="cb44d-377">Compiler.cs에서 스타일 문제를 정리(#10368)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-377">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-378">CommaDelimitedStringCollection에 사용되지 않는 형식 변환기를 제거(#11000)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-378">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-379">InitialSessionState.cs의 스타일을 정리(#10865)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-379">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-380">PSSession 클래스에 대해 코드 정리(#11001)</span><span class="sxs-lookup"><span data-stu-id="cb44d-380">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="cb44d-381">작동하지 않는 기능 'Get-Help가 처음 실행될 때 Get-Help에서 Update-Help를 실행'을 제거(#10974)</span><span class="sxs-lookup"><span data-stu-id="cb44d-381">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="cb44d-382">스타일 문제를 수정(#10998)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-382">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-383">정리: 기본 제공 형식 별칭을 사용(#10882)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-383">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-384">사용하지 않는 설정 키 ConsolePrompting을 제거하고 ExecutionPolicy 설정을 쿼리할 때 불필요한 문자열 생성을 방지(#10985)</span><span class="sxs-lookup"><span data-stu-id="cb44d-384">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="cb44d-385">일별 빌드에 대한 업데이트 알림 확인을 사용하지 않도록 설정(#10903)(@bergmeister에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-385">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="cb44d-386">#10338에서 손실된 디버깅 API를 복구(#10808)</span><span class="sxs-lookup"><span data-stu-id="cb44d-386">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="cb44d-387">더 이상 사용되지 않는 WorkflowJobSourceAdapter 참조를 제거(#10326)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-387">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-388">PreserveSig 특성을 수정하여 점프 목록 코드에서 COM 인터페이스를 정리(#9899)(@weltkante에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-388">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="cb44d-389">-Ia가 -InformationAction common 매개 변수용 별칭이 아닌 이유를 설명하는 주석을 추가(#10703)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-389">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-390">InvokeCommandCmdlet.cs의 이름을 InvokeExpressionCommand.cs로 변경(#10659)(@kilasuit에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-390">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="cb44d-391">업데이트 알림과 관련된 경미한 코드 정리를 추가(#10698)</span><span class="sxs-lookup"><span data-stu-id="cb44d-391">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="cb44d-392">원격 설치 스크립트에서 사용되지 않는 워크플로 논리를 제거(#10320)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-392">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-393">적절한 대/소문자를 사용하도록 도움말 형식을 업데이트(#10678)(@tnieto88에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-393">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="cb44d-394">지난달의 커밋에서 발생하는 CodeFactor 스타일 문제를 정리(#10591)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-394">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-395">PSTernaryOperator 실험적 기능에 대한 설명에서 오타를 수정(#10586)(@bergmeister에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-395">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="cb44d-396">ActionPreference.Suspend 열거형 값을 지원되지 않는 예약된 상태로 전환하고 기본 설정 변수에서 ActionPreference.Ignore 사용에 대한 제한을 제거(#10317)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-396">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-397">ArrayList를 List<T>로 바꿔 기능 변경 없이 코드를 더 읽기 쉽고 안정적으로 개선(#10333)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-397">Replace ArrayList with List<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-398">TestConnectionCommand 코드 스타일을 수정(#10439)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-398">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-399">AutomationEngine을 정리하고 불필요한 SetSessionStateDrive 메서드 호출을 제거(#10416)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-399">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-400">ConvertTo-Csv 및 ConvertFrom-Csv에 대한 기본 ParameterSetName의 이름을 다시 Delimiter로 변경(#10425)</span><span class="sxs-lookup"><span data-stu-id="cb44d-400">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="cb44d-401">도구</span><span class="sxs-lookup"><span data-stu-id="cb44d-401">Tools</span></span>

- <span data-ttu-id="cb44d-402">VS에서 빌드되는 SDKToUse 속성에 대한 기본 설정을 추가(#11085)</span><span class="sxs-lookup"><span data-stu-id="cb44d-402">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="cb44d-403">Install-Powershell.ps1: MSI 설치를 사용하기 위한 매개 변수를 추가(#10921)(@MJECloud에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-403">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="cb44d-404">install-powershell.ps1용 기본 예제를 추가(#10914)(@kilasuit에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-404">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="cb44d-405">Install-PowerShellRemoting.ps1을 사용하여 PowerShellHome 매개 변수에서 빈 문자열을 처리(#10526)(@Orca88에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-405">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="cb44d-406">install-powershell.sh에서 /etc/lsb-release를 /etc/os-release로 전환(#10773)(@Himura2la에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-406">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="cb44d-407">Windows에서 pwsh.exe 및 pwsh 일별 버전을 확인(#10738)(@centreboard에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-407">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="cb44d-408">installpsh-osx.sh에서 불필요한 탭을 제거(#10752)</span><span class="sxs-lookup"><span data-stu-id="cb44d-408">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="cb44d-409">이미 설치된 일별 빌드를 확인하도록 install-powershell.ps1를 업데이트(#10489)</span><span class="sxs-lookup"><span data-stu-id="cb44d-409">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="cb44d-410">테스트</span><span class="sxs-lookup"><span data-stu-id="cb44d-410">Tests</span></span>

- <span data-ttu-id="cb44d-411">안정적이지 않은 DSC 테스트를 보류(#11131)</span><span class="sxs-lookup"><span data-stu-id="cb44d-411">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="cb44d-412">해시 테이블의 키를 올바르게 확인하도록 stringdata 테스트를 수정(#10810)</span><span class="sxs-lookup"><span data-stu-id="cb44d-412">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="cb44d-413">테스트 모듈 언로드(#11061)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-413">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-414">테스트 URL 재시도 간격을 확대(#11015)</span><span class="sxs-lookup"><span data-stu-id="cb44d-414">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="cb44d-415">테스트 작업을 정확하게 설명하도록 테스트를 업데이트</span><span class="sxs-lookup"><span data-stu-id="cb44d-415">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="cb44d-416">(#10928)(@romero126에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-416">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="cb44d-417">신뢰도가 낮은 테스트 TestAppDomainProcessExitEvenHandlerNotLeaking을 임시로 건너뜀(#10827)</span><span class="sxs-lookup"><span data-stu-id="cb44d-417">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="cb44d-418">이벤트 처리기 누수 테스트를 안정적으로 개선(#10790)</span><span class="sxs-lookup"><span data-stu-id="cb44d-418">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="cb44d-419">CI YAML에서 대/소문자 구분 동기화(#10767)(@RDIL에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-419">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="cb44d-420">이벤트 처리기 누수 문제 해결을 위한 테스트를 추가(#10768)</span><span class="sxs-lookup"><span data-stu-id="cb44d-420">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="cb44d-421">Get-ChildItem 테스트를 추가(#10507)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-421">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-422">정확도를 위해 테스트의 모호한 언어를 스위치에서 매개 변수로 바꿈(#10666)(@romero126에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-422">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="cb44d-423">ForEach-Object -Parallel 테스트에 실험적 확인을 추가(#10354)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-423">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="cb44d-424">Alpine 유효성 검사에 대한 테스트를 업데이트(#10428)</span><span class="sxs-lookup"><span data-stu-id="cb44d-424">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="cb44d-425">빌드 및 패키지 개선 사항</span><span class="sxs-lookup"><span data-stu-id="cb44d-425">Build and Package Improvements</span></span>

- <span data-ttu-id="cb44d-426">조정 패키지 빌드에 대한 Nuget 패키지 서명을 수정(#11316)</span><span class="sxs-lookup"><span data-stu-id="cb44d-426">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="cb44d-427">PowerShell 갤러리 및 NuGet에서 종속성 업데이트(#11323)</span><span class="sxs-lookup"><span data-stu-id="cb44d-427">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="cb44d-428">Microsoft.ApplicationInsights를 2.11.0에서 2.12.0으로 변경(#11305)</span><span class="sxs-lookup"><span data-stu-id="cb44d-428">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="cb44d-429">Microsoft.CodeAnalysis.CSharp를 3.3.1에서 3.4.0으로 변경(#11265)</span><span class="sxs-lookup"><span data-stu-id="cb44d-429">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="cb44d-430">Debian 10 및 11용 패키지를 업데이트(#11236)</span><span class="sxs-lookup"><span data-stu-id="cb44d-430">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="cb44d-431">RC 이전에 실험적 기능만 활성화(#11162)</span><span class="sxs-lookup"><span data-stu-id="cb44d-431">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="cb44d-432">macOS 최소 버전 업데이트(#11163)</span><span class="sxs-lookup"><span data-stu-id="cb44d-432">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="cb44d-433">NJsonSchema를 10.0.27에서 10.0.28로 변경(#11170)</span><span class="sxs-lookup"><span data-stu-id="cb44d-433">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="cb44d-434">Preview.5의 README.md 및 metadata.json에서 링크를 업데이트(#10854)</span><span class="sxs-lookup"><span data-stu-id="cb44d-434">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="cb44d-435">PowerShell이 소유한 규정 준수 테스트용 파일 선택(#10837)</span><span class="sxs-lookup"><span data-stu-id="cb44d-435">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="cb44d-436">win7x86 msix 패키지 빌드를 허용</span><span class="sxs-lookup"><span data-stu-id="cb44d-436">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="cb44d-437">(내부 10515)</span><span class="sxs-lookup"><span data-stu-id="cb44d-437">(Internal 10515)</span></span>
- <span data-ttu-id="cb44d-438">의미 체계 버전을 NormalizeVersion 함수에 전달하도록 허용(#11087)</span><span class="sxs-lookup"><span data-stu-id="cb44d-438">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="cb44d-439">.NET Core 프레임워크를 3.1-preview.3으로 변경(#11079)</span><span class="sxs-lookup"><span data-stu-id="cb44d-439">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="cb44d-440">/src/Modules에서 PSReadLine을 2.0.0-beta5에서 2.0.0-beta6으로 변경(#11078)</span><span class="sxs-lookup"><span data-stu-id="cb44d-440">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="cb44d-441">Newtonsoft.Json을 12.0.2에서 12.0.3으로 변경(#11037)(#11038)</span><span class="sxs-lookup"><span data-stu-id="cb44d-441">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="cb44d-442">Debian 10, 11 및 CentOS 8 패키지 추가(#11028)</span><span class="sxs-lookup"><span data-stu-id="cb44d-442">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="cb44d-443">ReleaseDate 필드를 사용하여 Build-Info Json 파일을 업로드(#10986)</span><span class="sxs-lookup"><span data-stu-id="cb44d-443">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="cb44d-444">.NET Core 프레임워크를 3.1-preview.2로 변경(#10993)</span><span class="sxs-lookup"><span data-stu-id="cb44d-444">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="cb44d-445">x86 MSIX 패키지 빌드를 사용(#10934)</span><span class="sxs-lookup"><span data-stu-id="cb44d-445">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="cb44d-446">build.psm1에서 dotnet SDK 설치 스크립트 URL을 업데이트(#10927)</span><span class="sxs-lookup"><span data-stu-id="cb44d-446">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="cb44d-447">Markdig.Signed를 0.17.1에서 0.18.0으로 변경(#10887)</span><span class="sxs-lookup"><span data-stu-id="cb44d-447">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="cb44d-448">ThreadJob을 2.0.1에서 2.0.2으로 변경(#10886)</span><span class="sxs-lookup"><span data-stu-id="cb44d-448">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="cb44d-449">MS Store 요구 사항을 충족하도록 AppX Manifest 및 Packaging 모듈을 업데이트(#10878)</span><span class="sxs-lookup"><span data-stu-id="cb44d-449">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="cb44d-450">PowerShell SDK용 패키지 참조를 preview.5로 업데이트(내부 10295)</span><span class="sxs-lookup"><span data-stu-id="cb44d-450">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="cb44d-451">ThirdPartyNotices.txt를 업데이트(#10834)</span><span class="sxs-lookup"><span data-stu-id="cb44d-451">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="cb44d-452">Microsoft.PowerShell.Native를 7.0.0-preview.3으로 업데이트(#10826)</span><span class="sxs-lookup"><span data-stu-id="cb44d-452">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="cb44d-453">Microsoft.ApplicationInsights를 2.10.0에서 2.11.0으로 변경(#10608)</span><span class="sxs-lookup"><span data-stu-id="cb44d-453">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="cb44d-454">NJsonSchema를 10.0.24에서 10.0.27로 변경(#10756)</span><span class="sxs-lookup"><span data-stu-id="cb44d-454">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="cb44d-455">빌드 시스템에 MacPorts 지원을 추가(#10736)(@Lucius-Q-User에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-455">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="cb44d-456">PackageManagement를 1.4.4에서 1.4.5로 변경(#10728)</span><span class="sxs-lookup"><span data-stu-id="cb44d-456">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="cb44d-457">NJsonSchema를 10.0.23에서 10.0.24로 변경(#10635)</span><span class="sxs-lookup"><span data-stu-id="cb44d-457">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="cb44d-458">MSI에서 클라이언트/서버 원격 분석을 구분하는 환경 변수를 추가(#10612)</span><span class="sxs-lookup"><span data-stu-id="cb44d-458">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="cb44d-459">PSDesiredStateConfiguration을 2.0.3에서 2.0.4로 변경(#10603)</span><span class="sxs-lookup"><span data-stu-id="cb44d-459">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="cb44d-460">Microsoft.CodeAnalysis.CSharp를 3.2.1에서 3.3.1로 변경(#10607)</span><span class="sxs-lookup"><span data-stu-id="cb44d-460">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="cb44d-461">.Net Core 3.0 RTM으로 업데이트(#10604)(@bergmeister에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-461">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="cb44d-462">Microsoft Store 요구 사항에 맞게 MSIX 패키지 버전을 업데이트(#10588)</span><span class="sxs-lookup"><span data-stu-id="cb44d-462">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="cb44d-463">PowerShellGet 버전을 2.2에서 2.2.1로 변경(#10382)</span><span class="sxs-lookup"><span data-stu-id="cb44d-463">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="cb44d-464">PackageManagement 버전을 1.4.3에서 1.4.4로 변경(#10383)</span><span class="sxs-lookup"><span data-stu-id="cb44d-464">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="cb44d-465">7\.0.0-preview.4용 README.md 및 metadata.json을 업데이트(#10011)</span><span class="sxs-lookup"><span data-stu-id="cb44d-465">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="cb44d-466">.NET Core 3.0 버전을 미리 보기 9에서 RC1로 업그레이드(#10552)(@bergmeister에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-466">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="cb44d-467">ExperimentalFeature 목록 생성을 수정(내부 9996)</span><span class="sxs-lookup"><span data-stu-id="cb44d-467">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="cb44d-468">PSReadLine 버전을 2.0.0-beta4에서 2.0.0-beta5로 변경(#10536)</span><span class="sxs-lookup"><span data-stu-id="cb44d-468">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="cb44d-469">릴리스 태그를 설정하는 릴리스 빌드 스크립트를 수정</span><span class="sxs-lookup"><span data-stu-id="cb44d-469">Fix release build script to set release tag</span></span>
- <span data-ttu-id="cb44d-470">Microsoft.PowerShell.Native 버전을 7.0.0-preview.2로 업데이트(#10519)</span><span class="sxs-lookup"><span data-stu-id="cb44d-470">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="cb44d-471">Netcoreapp3.0 preview9로 업그레이드(#10484)(@bergmeister에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-471">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="cb44d-472">일별 조정 빌드가 일별 빌드임을 인식(#10464)</span><span class="sxs-lookup"><span data-stu-id="cb44d-472">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="cb44d-473">결합된 패키지 빌드를 업데이트하여 일별 빌드를 릴리스(#10449)</span><span class="sxs-lookup"><span data-stu-id="cb44d-473">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="cb44d-474">appveyor 참조를 제거(#10445)(@RDIL에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-474">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="cb44d-475">NJsonSchema 버전을 10.0.22에서 10.0.23으로 변경(#10421)</span><span class="sxs-lookup"><span data-stu-id="cb44d-475">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="cb44d-476">Alpine에 대한 일부 종속성에 필요하므로 linux-x64 빌드 폴더 삭제를 제거(#10407)</span><span class="sxs-lookup"><span data-stu-id="cb44d-476">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="cb44d-477">설명서 및 도움말 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="cb44d-477">Documentation and Help Content</span></span>

- <span data-ttu-id="cb44d-478">변경 로그를 릴리스당 단일 로그로 리팩터링(#11165)</span><span class="sxs-lookup"><span data-stu-id="cb44d-478">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="cb44d-479">PowerShell 7 온라인 도움말 문서용 FWLinks를 수정(#11071)</span><span class="sxs-lookup"><span data-stu-id="cb44d-479">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="cb44d-480">CONTRIBUTING.md를 업데이트(#11096)(@mklement0에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-480">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="cb44d-481">README.md에서 설치 문서 링크를 수정(#11083)</span><span class="sxs-lookup"><span data-stu-id="cb44d-481">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="cb44d-482">install-powershell.ps1 스크립트에 예제를 추가(#11024)(@kilasuit에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-482">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="cb44d-483">CHANGELOG.md에서 Select-String 강조 및 Import-DscResource를 수정(#10890)</span><span class="sxs-lookup"><span data-stu-id="cb44d-483">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="cb44d-484">powershell-beginners-guide.md에서 만료된 링크를 제거(#10926)</span><span class="sxs-lookup"><span data-stu-id="cb44d-484">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="cb44d-485">안정적 및 서비스 변경 로그를 병합(#10527)</span><span class="sxs-lookup"><span data-stu-id="cb44d-485">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="cb44d-486">빌드 문서에서 사용된 .NET 버전을 업데이트(#10775)(@Greg-Smulko에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-486">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="cb44d-487">powershell-beginners-guide.md에서 링크를 MSDN에서 docs.microsoft.com으로 바꿈(#10778)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-487">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="cb44d-488">끊어진 DSC 개요 링크 수정(#10702)</span><span class="sxs-lookup"><span data-stu-id="cb44d-488">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="cb44d-489">Support_Question.md를 업데이트하여 Stack Overflow에 다른 커뮤니티 리소스로 연결(#10638)(@mklement0에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-489">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="cb44d-490">배포 요청 템플릿에 프로세서 아키텍처 추가(#10661)</span><span class="sxs-lookup"><span data-stu-id="cb44d-490">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="cb44d-491">PowerShell 학습 문서에 새로운 PowerShell MoL 도서 추가(#10602)</span><span class="sxs-lookup"><span data-stu-id="cb44d-491">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="cb44d-492">v6.1.6 및 v6.2.3 릴리스용 README.md와 메타데이터를 업데이터(#10523)</span><span class="sxs-lookup"><span data-stu-id="cb44d-492">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="cb44d-493">README.md에서 오타를 수정(#10465)(@vedhasp에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-493">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="cb44d-494">학습 리소스 문서에 PSKoans 모듈에 대한 참조를 추가(#10369)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="cb44d-494">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="cb44d-495">7\.0.0-preview.3용 README.md 및 metadata.json을 업데이트(#10393)</span><span class="sxs-lookup"><span data-stu-id="cb44d-495">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
