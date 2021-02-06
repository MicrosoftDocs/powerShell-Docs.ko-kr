---
description: 다른 버전의 PowerShell은 서로 다른 기본 런타임에서 실행 됩니다.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 3b1b938874b36919a1a0627f3b492cbc961e4a2f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599601"
---
# <a name="about-powershell-editions"></a><span data-ttu-id="9302e-103">PowerShell 버전 정보</span><span class="sxs-lookup"><span data-stu-id="9302e-103">About PowerShell Editions</span></span>

## <a name="short-description"></a><span data-ttu-id="9302e-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9302e-104">Short Description</span></span>
<span data-ttu-id="9302e-105">다른 버전의 PowerShell은 서로 다른 기본 런타임에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-105">Different editions of PowerShell run on different underlying runtimes.</span></span>

## <a name="long-description"></a><span data-ttu-id="9302e-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9302e-106">Long Description</span></span>

<span data-ttu-id="9302e-107">PowerShell 5.1에는 각각 서로 다른 .NET 런타임에서 실행 되는 여러 *버전* 의 powershell이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-107">From PowerShell 5.1, there are multiple *editions* of PowerShell that each run on a different .NET runtime.</span></span> <span data-ttu-id="9302e-108">PowerShell 6.2을 통해 PowerShell에는 두 가지 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-108">As of PowerShell 6.2 there are two editions of PowerShell:</span></span>

- <span data-ttu-id="9302e-109">.NET Framework에서 실행 되는 **데스크톱**</span><span class="sxs-lookup"><span data-stu-id="9302e-109">**Desktop**, which runs on .NET Framework.</span></span> <span data-ttu-id="9302e-110">Windows 데스크톱, Windows Server, Windows Server Core 및 대부분의 다른 Windows 운영 체제와 같은 완전 한 기능을 갖춘 Windows 버전의 powershell 5.1 뿐만 아니라 PowerShell 4는 데스크톱 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-110">PowerShell 4 and below, as well as PowerShell 5.1 on full-featured Windows editions like Windows Desktop, Windows Server, Windows Server Core and most other Windows operating systems are Desktop edition.</span></span>
  <span data-ttu-id="9302e-111">이는 원래 PowerShell 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-111">This is the original PowerShell edition.</span></span>
- <span data-ttu-id="9302e-112">**Core**-.net core에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-112">**Core**, which runs on .NET Core.</span></span> <span data-ttu-id="9302e-113">.NET Framework를 사용할 수 없는 windows Nano Server 및 Windows IoT와 같은 일부 공간을 차지 하는 windows 버전의 powershell 5.1 뿐만 아니라 PowerShell 6.0 이상.</span><span class="sxs-lookup"><span data-stu-id="9302e-113">PowerShell 6.0 and above, as well as PowerShell 5.1 on some reduced-footprint Windows editions such as Windows Nano Server and Windows IoT where .NET Framework is unavailable.</span></span>

<span data-ttu-id="9302e-114">PowerShell 버전은 .net 런타임에 해당 하므로 .NET API 및 PowerShell 모듈 호환성의 기본 표시기입니다. 일부 .NET Api, 형식 또는 메서드는 두 .NET 런타임 모두에서 사용할 수 없으며이에 종속 된 PowerShell 스크립트 및 모듈에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-114">Because the edition of PowerShell corresponds to its .NET runtime, it is the primary indicator of .NET API and PowerShell module compatibility; some .NET APIs, types or methods are not available in both .NET runtimes and this affects PowerShell scripts and modules that depend on them.</span></span>

## <a name="the-psedition-automatic-variable"></a><span data-ttu-id="9302e-115">`$PSEdition`자동 변수</span><span class="sxs-lookup"><span data-stu-id="9302e-115">The `$PSEdition` automatic variable</span></span>

<span data-ttu-id="9302e-116">PowerShell 5.1 이상에서는 자동 변수를 사용 하 여 실행 중인 버전을 확인할 수 있습니다 `$PSEdition` .</span><span class="sxs-lookup"><span data-stu-id="9302e-116">In PowerShell 5.1 and above, you can find out what edition you are running with the `$PSEdition` automatic variable:</span></span>

```powershell
$PSEdition
```

```Output
Core
```

<span data-ttu-id="9302e-117">PowerShell 4이 하에서이 변수는 존재 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-117">In PowerShell 4 and below, this variable does not exist.</span></span> <span data-ttu-id="9302e-118">`$PSEdition` null 인 경우 값을 갖는 것과 동일 하 게 처리 되어야 합니다 `Desktop` .</span><span class="sxs-lookup"><span data-stu-id="9302e-118">`$PSEdition` being null should be treated as the same as having the value `Desktop`.</span></span>

### <a name="edition-in-psversiontable"></a><span data-ttu-id="9302e-119">의 버전 `$PSVersionTable`</span><span class="sxs-lookup"><span data-stu-id="9302e-119">Edition in `$PSVersionTable`</span></span>

<span data-ttu-id="9302e-120">`$PSVersionTable`또한 자동 변수는 PowerShell 5.1 이상 버전 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-120">The `$PSVersionTable` automatic variable also has edition information in PowerShell 5.1 and above:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

<span data-ttu-id="9302e-121">`PSEdition`필드는 자동 변수와 동일한 값을 갖습니다 `$PSEdition` .</span><span class="sxs-lookup"><span data-stu-id="9302e-121">The `PSEdition` field will have the same value as the `$PSEdition` automatic variable.</span></span>

## <a name="the-compatiblepseditions-module-manifest-field"></a><span data-ttu-id="9302e-122">`CompatiblePSEditions`모듈 매니페스트 필드</span><span class="sxs-lookup"><span data-stu-id="9302e-122">The `CompatiblePSEditions` module manifest field</span></span>

<span data-ttu-id="9302e-123">PowerShell 모듈은 모듈 매니페스트의 필드를 사용 하 여 호환 되는 PowerShell 버전을 선언할 수 있습니다 `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="9302e-123">PowerShell modules can declare what editions of PowerShell they are compatible with using the `CompatiblePSEditions` field of the module manifest.</span></span>

<span data-ttu-id="9302e-124">예를 들어 모듈 매니페스트는 `Desktop` 및 `Core` 버전의 PowerShell과의 호환성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-124">For example, a module manifest declaring compatibility with both `Desktop` and `Core` editions of PowerShell:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

<span data-ttu-id="9302e-125">호환성이 있는 모듈 매니페스트의 예는 `Desktop` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-125">An example of a module manifest with only `Desktop` compatibility:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

<span data-ttu-id="9302e-126">`CompatiblePSEditions` `Desktop` 이 필드 앞에 생성 된 모듈이이 버전에 대해 암시적으로 작성 되었으므로 모듈 매니페스트에서 필드를 생략 하면로 설정 하는 것과 동일한 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-126">Omitting the `CompatiblePSEditions` field from a module manifest will have the same effect as setting it to `Desktop`, since modules created before this field was introduced were implicitly written for this edition.</span></span>

<span data-ttu-id="9302e-127">Windows의 일부로 제공 되지 않은 모듈 (예: 갤러리에서 작성 하거나 설치 하는 모듈)의 경우이 필드는 정보 제공 용입니다. PowerShell은 필드를 기반으로 하는 동작을 변경 하지 `CompatiblePSEditions` 않지만 `PSModuleInfo` 사용자의 논리에 따라 개체 (에 의해 반환 됨)에이를 노출 합니다 `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="9302e-127">For modules not shipped as part of Windows (i.e. modules you write or install from the gallery), this field is informational only; PowerShell does not change behavior based on the `CompatiblePSEditions` field, but does expose it on the `PSModuleInfo` object (returned by `Get-Module`) for your own logic:</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> <span data-ttu-id="9302e-128">`CompatiblePSEditions`모듈 필드는 PowerShell 5.1 이상 에서만 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-128">The `CompatiblePSEditions` module field is only compatible with PowerShell 5.1 and above.</span></span>
> <span data-ttu-id="9302e-129">이 필드를 포함 하면 모듈이 PowerShell 4와 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-129">Including this field will cause a module to be incompatible with PowerShell 4 and below.</span></span>
> <span data-ttu-id="9302e-130">필드는 전적으로 정보를 제공 하기 때문에 이후 PowerShell 버전에서 안전 하 게 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-130">Since the field is purely informational, it can be safely omitted in later PowerShell versions.</span></span>

<span data-ttu-id="9302e-131">PowerShell 6.1에서 `Get-Module -ListAvailable` 포맷터는 각 모듈의 버전 호환성을 표시 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-131">In PowerShell 6.1, `Get-Module -ListAvailable` has had its formatter updated to display the edition-compatibility of each module:</span></span>

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a><span data-ttu-id="9302e-132">버전-Windows의 일부로 제공 되는 모듈에 대 한 호환성</span><span class="sxs-lookup"><span data-stu-id="9302e-132">Edition-compatibility for modules that ship as part of Windows</span></span>

<span data-ttu-id="9302e-133">Windows의 일부로 제공 되거나 역할이 나 기능의 일부로 설치 된 모듈의 경우 PowerShell 6.1 이상에서 `CompatiblePSEditions` 필드를 다르게 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-133">For modules that come as part of Windows (or are installed as part of a role or feature), PowerShell 6.1 and above treat the `CompatiblePSEditions` field differently.</span></span> <span data-ttu-id="9302e-134">이러한 모듈은 Windows PowerShell 시스템 모듈 디렉터리 ()에서 찾을 수 있습니다 `%windir%\System\WindowsPowerShell\v1.0\Modules` .</span><span class="sxs-lookup"><span data-stu-id="9302e-134">Such modules are found in the Windows PowerShell system modules directory (`%windir%\System\WindowsPowerShell\v1.0\Modules`).</span></span>

<span data-ttu-id="9302e-135">이 디렉터리에서 로드 되거나 검색 된 모듈의 경우 PowerShell 6.1 이상에서는 필드를 사용 하 여 `CompatiblePSEditions` 모듈이 현재 세션과 호환 되는지 여부를 확인 하 고 적절 하 게 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-135">For modules loaded from or found in this directory, PowerShell 6.1 and above uses the `CompatiblePSEditions` field to determine whether the module will be compatible with the current session and behaves accordingly.</span></span>

<span data-ttu-id="9302e-136">`Import-Module`을 사용 하는 경우에 없는 모듈을 `Core` 가져오지 않고 `CompatiblePSEditions` 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-136">When `Import-Module` is used, a module without `Core` in `CompatiblePSEditions` will not be imported and an error will be displayed:</span></span>

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

<span data-ttu-id="9302e-137">`Get-Module -ListAvailable`을 사용 하는 경우에 없는 모듈 `Core` `CompatiblePSEditions` 은 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-137">When `Get-Module -ListAvailable` is used, modules without `Core` in `CompatiblePSEditions` will not be displayed:</span></span>

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

<span data-ttu-id="9302e-138">두 경우 모두 `-SkipEditionCheck` switch 매개 변수를 사용 하 여이 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-138">In both cases, the `-SkipEditionCheck` switch parameter can be used to override this behavior:</span></span>

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> <span data-ttu-id="9302e-139">`Import-Module -SkipEditionCheck` 모듈에 대해 성공한 것 처럼 보일 수 있지만,이 모듈을 사용 하면 나중에 비 호환성이 발생할 위험이 있습니다. 처음에는 모듈을 로드 하는 데 성공 하지만 나중에 명령이 호환 되지 않는 API를 호출 하 고 자연스럽 게 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-139">`Import-Module -SkipEditionCheck` may appear to succeed for a module, but using that module runs the risk of encountering an incompatibility later on; while loading the module initially succeeds, a command may later call an incompatible API and fail spontaneously.</span></span>

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a><span data-ttu-id="9302e-140">버전 간 호환성을 위한 PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="9302e-140">Authoring PowerShell modules for edition cross-compatibility</span></span>

<span data-ttu-id="9302e-141">Powershell 모듈을 작성 하 여 및 버전의 PowerShell을 모두 대상으로 하는 경우 `Desktop` `Core` 버전 간 호환성을 위해 수행할 수 있는 작업이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-141">When writing a PowerShell module to target both `Desktop` and `Core` editions of PowerShell, there are things you can do to ensure cross-edition compatibility.</span></span>

<span data-ttu-id="9302e-142">그러나 호환성을 확인 하 고 지속적으로 유효성을 검사 하는 유일한 방법은 스크립트 또는 모듈에 대 한 테스트를 작성 하 고와 호환성이 필요한 PowerShell의 모든 버전 및 버전에서 실행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-142">The only true way to confirm and continually validate compatibility however is to write tests for your script or module and run them on all versions and editions of PowerShell you need compatibility with.</span></span> <span data-ttu-id="9302e-143">이에 대 한 권장 테스트 프레임 워크는 [Pester][]입니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-143">A recommended testing framework for this is [Pester][].</span></span>

### <a name="powershell-script"></a><span data-ttu-id="9302e-144">PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="9302e-144">PowerShell script</span></span>

<span data-ttu-id="9302e-145">PowerShell은 버전 간에 동일 하 게 작동 합니다. 버전 호환성의 영향을 받는 cmdlet, 모듈 및 .NET Api를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-145">As a language, PowerShell works the same between editions; it is the cmdlets, modules and .NET APIs you use that are affected by edition compatibility.</span></span>

<span data-ttu-id="9302e-146">일반적으로 PowerShell 6.1 이상에서 작동 하는 스크립트는 Windows PowerShell 5.1에서 작동 하지만 몇 가지 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-146">Generally, scripts that work in PowerShell 6.1 and above will work with Windows PowerShell 5.1, but there are some exceptions.</span></span>

<span data-ttu-id="9302e-147">버전 1.18.0 [Psscriptanalyzer][] 모듈에는 [`PSUseCompatibleCommands`][] [`PSUseCompatibleTypes`][] PowerShell 스크립트에서 호환 되지 않는 명령 및 .net api 사용을 검색할 수 있는 및와 같은 규칙이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-147">Version 1.18.0 [PSScriptAnalyzer][] module has rules like [`PSUseCompatibleCommands`][] and [`PSUseCompatibleTypes`][] that are able to detect possibly incompatible usage of commands and .NET APIs in PowerShell scripts.</span></span>

### <a name="net-assemblies"></a><span data-ttu-id="9302e-148">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="9302e-148">.NET assemblies</span></span>

<span data-ttu-id="9302e-149">소스 코드에서 생성 된 .NET 어셈블리 (Dll)를 통합 하는 모듈 또는 이진 모듈을 작성 하는 경우 .NET 및 PowerShell API 호환성의 컴파일 타임 호환성 유효성 검사를 위해 [.NET Standard][] 및 [powershell 표준][] 에 대해 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-149">If you are writing a binary module or a module that incorporates .NET assemblies (DLLs) generated from source code, you should compile against [.NET Standard][] and [PowerShell Standard][] for compile-time compatibility validation of .NET and PowerShell API compatibility.</span></span>

<span data-ttu-id="9302e-150">이러한 라이브러리는 컴파일 시간에 일부 호환성을 확인할 수 있지만 버전 간에 가능한 동작 차이를 catch 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-150">Although these libraries are able to check some compatibility at compile time, they won't be able to catch possible behavioral differences between editions.</span></span> <span data-ttu-id="9302e-151">이렇게 하려면 여전히 테스트를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9302e-151">For this you must still write tests.</span></span>

## <a name="see-also"></a><span data-ttu-id="9302e-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9302e-152">See also</span></span>

- [<span data-ttu-id="9302e-153">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="9302e-153">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="9302e-154">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="9302e-154">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="9302e-155">Get-Module</span><span class="sxs-lookup"><span data-stu-id="9302e-155">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)
- [<span data-ttu-id="9302e-156">호환되는 PowerShell 버전이 있는 모듈</span><span class="sxs-lookup"><span data-stu-id="9302e-156">Modules with compatible PowerShell Editions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[`PSUseCompatibleCommands`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[`PSUseCompatibleTypes`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
