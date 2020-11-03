---
description: 필요한 요소 없이 스크립트가 실행 되지 않도록 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: d499499c58f22bff10d712d33fc3a021e4fa6bbb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222578"
---
# <a name="about-requires"></a><span data-ttu-id="deb15-104">필요한 정보</span><span class="sxs-lookup"><span data-stu-id="deb15-104">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="deb15-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="deb15-105">Short description</span></span>
<span data-ttu-id="deb15-106">필요한 요소 없이 스크립트가 실행 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-106">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="deb15-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-107">Long description</span></span>

<span data-ttu-id="deb15-108">`#Requires`문은 PowerShell 버전, 모듈 (및 버전) 또는 스냅인 (및 버전) 및 버전 필수 구성 요소가 충족 되지 않으면 스크립트가 실행 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-108">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="deb15-109">필수 구성 요소가 충족 되지 않으면 PowerShell에서 스크립트를 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-109">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="deb15-110">구문</span><span class="sxs-lookup"><span data-stu-id="deb15-110">Syntax</span></span>

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="deb15-111">구문에 대 한 자세한 내용은 [Scriptrequirements 사항](/dotnet/api/system.management.automation.language.scriptrequirements)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="deb15-111">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="deb15-112">사용할 규칙</span><span class="sxs-lookup"><span data-stu-id="deb15-112">Rules for use</span></span>

<span data-ttu-id="deb15-113">스크립트는 둘 이상의 문을 포함할 수 있습니다 `#Requires` .</span><span class="sxs-lookup"><span data-stu-id="deb15-113">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="deb15-114">`#Requires`문은 스크립트의 모든 줄에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-114">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="deb15-115">`#Requires`문을 함수 안에 두면 해당 범위가 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-115">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="deb15-116">모든 `#Requires` 문은 항상 전역적으로 적용 되며 스크립트가 실행 되기 전에 충족 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-116">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="deb15-117">`#Requires`스크립트의 모든 줄에 문이 표시 될 수 있지만 스크립트의 해당 위치는 응용 프로그램의 순서에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-117">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="deb15-118">`#Requires`스크립트를 실행 하기 전에 문이 제공 하는 전역 상태를 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-118">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="deb15-119">예제:</span><span class="sxs-lookup"><span data-stu-id="deb15-119">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="deb15-120">필요한 모듈이 문 앞에서 제거 되었으므로 위의 코드는 실행 되지 않는 것으로 간주할 수 있습니다 `#Requires` .</span><span class="sxs-lookup"><span data-stu-id="deb15-120">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="deb15-121">그러나 `#Requires` 스크립트를 실행 하기 전에 상태를 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-121">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="deb15-122">그런 다음 스크립트의 첫 번째 줄에서 필요한 상태를 무효화 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-122">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="deb15-123">매개 변수</span><span class="sxs-lookup"><span data-stu-id="deb15-123">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="deb15-124">-어셈블리 \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="deb15-124">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

<span data-ttu-id="deb15-125">어셈블리 DLL 파일 또는 .NET 어셈블리 이름에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-125">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="deb15-126">**Assembly** 매개 변수는 PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-126">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="deb15-127">.NET 어셈블리에 대 한 자세한 내용은 [어셈블리 이름](/dotnet/standard/assembly/names)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="deb15-127">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="deb15-128">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="deb15-128">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="deb15-129">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="deb15-129">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="deb15-130">스크립트에 필요한 PowerShell의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-130">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="deb15-131">주 버전 번호 및 부 버전 번호 (선택 사항)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-131">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="deb15-132">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="deb15-132">For example:</span></span>

```powershell
#Requires -Version 5.1
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="deb15-133">-Add-pssnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="deb15-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="deb15-134">스크립트에 필요한 PowerShell 스냅인을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-134">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="deb15-135">스냅인 이름과 버전 번호 (선택 사항)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-135">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="deb15-136">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="deb15-136">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="deb15-137">-모듈 \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="deb15-137">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="deb15-138">스크립트에 필요한 PowerShell 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-138">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="deb15-139">모듈 이름 및 버전 번호 (선택 사항)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-139">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="deb15-140">필수 모듈이 현재 세션에 없으면 PowerShell에서 해당 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-140">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="deb15-141">모듈을 가져올 수 없는 경우 PowerShell에서 종료 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-141">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="deb15-142">각 모듈에 대해 모듈 이름 ( \<String\> ) 또는 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-142">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="deb15-143">값은 문자열과 해시 테이블의 조합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-143">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="deb15-144">해시 테이블에는 다음과 같은 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-144">The hash table has the following keys.</span></span>

- <span data-ttu-id="deb15-145">`ModuleName` - **필수** 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-145">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="deb15-146">`GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-146">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="deb15-147">또한 아래 세 키 중 하나를 지정 **해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-147">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="deb15-148">이러한 키는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-148">These keys can't be used together.</span></span>
  - <span data-ttu-id="deb15-149">`ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-149">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="deb15-150">`RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-150">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="deb15-151">`MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-151">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="deb15-152">`RequiredVersion` 는 Windows PowerShell 5.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-152">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="deb15-153">`MaximumVersion` 는 Windows PowerShell 5.1에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-153">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="deb15-154">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="deb15-154">For example:</span></span>

<span data-ttu-id="deb15-155">`Hyper-V`(버전 `1.1` 이상)이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-155">Require that `Hyper-V` (version `1.1` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; ModuleVersion="1.1" }
```

<span data-ttu-id="deb15-156">에는 `Hyper-V` ( **only** 버전만 `1.1` )이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-156">Requires that `Hyper-V` ( **only** version `1.1`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="1.1" }
```

<span data-ttu-id="deb15-157">`Hyper-V`(버전 `1.1` 이상)이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-157">Requires that `Hyper-V` (version `1.1` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; MaximumVersion="1.1" }
```

<span data-ttu-id="deb15-158">에는 및의 모든 `PSScheduledJob` 버전이 `PSWorkflow` 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-158">Requires that any version of `PSScheduledJob` and `PSWorkflow`, is installed.</span></span>

```powershell
#Requires -Modules PSWorkflow, PSScheduledJob
```

<span data-ttu-id="deb15-159">키를 사용 하는 경우 `RequiredVersion` 버전 문자열이 필요한 버전 문자열과 정확 하 게 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-159">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you wish to require.</span></span>

```powershell
Get-Module Hyper-V
```

```Output
ModuleType Version    Name     ExportedCommands
---------- -------    ----     ------------------
Binary     2.0.0.0    hyper-v  {Add-VMAssignableDevice, ...}
```

<span data-ttu-id="deb15-160">**2.0.0** 가 **2.0.0.0** 과 정확히 일치 하지 않기 때문에 다음 예제는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-160">The following example fails because **2.0.0** doesn't exactly match **2.0.0.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="2.0.0" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="deb15-161">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="deb15-161">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="deb15-162">스크립트에 필요한 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-162">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="deb15-163">유효한 값은 PowerShell Core에 대 한 **Core** 및 Windows Powershell의 **데스크톱** 입니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-163">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="deb15-164">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="deb15-164">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="deb15-165">-ShellId</span><span class="sxs-lookup"><span data-stu-id="deb15-165">-ShellId</span></span>

<span data-ttu-id="deb15-166">스크립트에 필요한 셸을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-166">Specifies the shell that the script requires.</span></span> <span data-ttu-id="deb15-167">셸 ID를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-167">Enter the shell ID.</span></span> <span data-ttu-id="deb15-168">**ShellId** 매개 변수를 사용 하는 경우 **add-pssnapin** 매개 변수도 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-168">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="deb15-169">자동 변수를 쿼리하여 현재 **ShellId** 을 찾을 수 있습니다 `$ShellId` .</span><span class="sxs-lookup"><span data-stu-id="deb15-169">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="deb15-170">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="deb15-170">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="deb15-171">이 매개 변수는 더 이상 사용 되지 않는 미니 셸에서 사용 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-171">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="deb15-172">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="deb15-172">-RunAsAdministrator</span></span>

<span data-ttu-id="deb15-173">이 스위치 매개 변수는 문에 추가 될 때 스크립트를 실행 하는 `#Requires` PowerShell 세션을 관리자 권한으로 시작 해야 함을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-173">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="deb15-174">**RunAsAdministrator** 매개 변수는 Windows 이외의 운영 체제에서 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-174">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="deb15-175">**RunAsAdministrator** 매개 변수는 PowerShell 4.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-175">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="deb15-176">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-176">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="deb15-177">예</span><span class="sxs-lookup"><span data-stu-id="deb15-177">Examples</span></span>

<span data-ttu-id="deb15-178">다음 스크립트에는 두 개의 `#Requires` 문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-178">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="deb15-179">두 문에 지정 된 요구 사항이 충족 되지 않으면 스크립트가 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-179">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="deb15-180">각 `#Requires` 문은 줄의 첫 번째 항목 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="deb15-180">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules PSWorkflow
#Requires -Version 3
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="deb15-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="deb15-181">See also</span></span>

[<span data-ttu-id="deb15-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="deb15-182">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="deb15-183">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="deb15-183">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="deb15-184">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="deb15-184">about_PSSnapins</span></span>](about_PSSnapins.md)

[<span data-ttu-id="deb15-185">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="deb15-185">Get-PSSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)
