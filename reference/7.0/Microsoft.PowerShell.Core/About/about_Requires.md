---
description: 필요한 요소 없이 스크립트가 실행 되지 않도록 합니다.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: 73c225f493fb671b34925d0127cc0d5cff0ab33e
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490587"
---
# <a name="about-requires"></a><span data-ttu-id="acb11-103">필요한 정보</span><span class="sxs-lookup"><span data-stu-id="acb11-103">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="acb11-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="acb11-104">Short description</span></span>
<span data-ttu-id="acb11-105">필요한 요소 없이 스크립트가 실행 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-105">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="acb11-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-106">Long description</span></span>

<span data-ttu-id="acb11-107">`#Requires`문은 PowerShell 버전, 모듈 (및 버전) 또는 스냅인 (및 버전) 및 버전 필수 구성 요소가 충족 되지 않으면 스크립트가 실행 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-107">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="acb11-108">필수 구성 요소가 충족 되지 않으면 PowerShell에서 스크립트를 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-108">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="acb11-109">구문</span><span class="sxs-lookup"><span data-stu-id="acb11-109">Syntax</span></span>

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="acb11-110">구문에 대 한 자세한 내용은 [Scriptrequirements 사항](/dotnet/api/system.management.automation.language.scriptrequirements)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="acb11-110">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="acb11-111">사용할 규칙</span><span class="sxs-lookup"><span data-stu-id="acb11-111">Rules for use</span></span>

<span data-ttu-id="acb11-112">스크립트는 둘 이상의 문을 포함할 수 있습니다 `#Requires` .</span><span class="sxs-lookup"><span data-stu-id="acb11-112">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="acb11-113">`#Requires`문은 스크립트의 모든 줄에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-113">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="acb11-114">`#Requires`문을 함수 안에 두면 해당 범위가 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-114">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="acb11-115">모든 `#Requires` 문은 항상 전역적으로 적용 되며 스크립트가 실행 되기 전에 충족 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-115">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="acb11-116">`#Requires`스크립트의 모든 줄에 문이 표시 될 수 있지만 스크립트의 해당 위치는 응용 프로그램의 순서에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-116">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="acb11-117">`#Requires`스크립트를 실행 하기 전에 문이 제공 하는 전역 상태를 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-117">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="acb11-118">예제:</span><span class="sxs-lookup"><span data-stu-id="acb11-118">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="acb11-119">필요한 모듈이 문 앞에서 제거 되었으므로 위의 코드는 실행 되지 않는 것으로 간주할 수 있습니다 `#Requires` .</span><span class="sxs-lookup"><span data-stu-id="acb11-119">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="acb11-120">그러나 `#Requires` 스크립트를 실행 하기 전에 상태를 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-120">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="acb11-121">그런 다음 스크립트의 첫 번째 줄에서 필요한 상태를 무효화 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-121">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="acb11-122">매개 변수</span><span class="sxs-lookup"><span data-stu-id="acb11-122">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="acb11-123">-어셈블리 \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="acb11-123">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

> [!IMPORTANT]
> <span data-ttu-id="acb11-124">`-Assembly`구문은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-124">The `-Assembly` syntax is deprecated.</span></span> <span data-ttu-id="acb11-125">함수를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-125">It serves no function.</span></span> <span data-ttu-id="acb11-126">구문이 PowerShell 5.1에 추가 되었지만 지원 코드는 구현 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-126">The syntax was added in PowerShell 5.1 but the supporting code was never implemented.</span></span> <span data-ttu-id="acb11-127">구문은 이전 버전과의 호환성을 위해 계속 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-127">The syntax is still accepted for backward compatibility.</span></span>

<span data-ttu-id="acb11-128">어셈블리 DLL 파일 또는 .NET 어셈블리 이름에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-128">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="acb11-129">**Assembly** 매개 변수는 PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-129">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="acb11-130">.NET 어셈블리에 대 한 자세한 내용은 [어셈블리 이름](/dotnet/standard/assembly/names)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="acb11-130">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="acb11-131">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-131">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="acb11-132">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="acb11-132">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="acb11-133">스크립트에 필요한 PowerShell의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-133">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="acb11-134">주 버전 번호 및 부 버전 번호 (선택 사항)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-134">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="acb11-135">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-135">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="acb11-136">-Add-pssnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="acb11-136">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="acb11-137">스크립트에 필요한 PowerShell 스냅인을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-137">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="acb11-138">스냅인 이름과 버전 번호 (선택 사항)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-138">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="acb11-139">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-139">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="acb11-140">-모듈 \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="acb11-140">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="acb11-141">스크립트에 필요한 PowerShell 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-141">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="acb11-142">모듈 이름 및 버전 번호 (선택 사항)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-142">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="acb11-143">필수 모듈이 현재 세션에 없으면 PowerShell에서 해당 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-143">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="acb11-144">모듈을 가져올 수 없는 경우 PowerShell에서 종료 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-144">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="acb11-145">각 모듈에 대해 모듈 이름 ( \<String\> ) 또는 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-145">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="acb11-146">값은 문자열과 해시 테이블의 조합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-146">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="acb11-147">해시 테이블에는 다음과 같은 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-147">The hash table has the following keys.</span></span>

- <span data-ttu-id="acb11-148">`ModuleName` - **필수** 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-148">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="acb11-149">`GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-149">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="acb11-150">또한 아래 세 키 중 하나를 지정 **해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-150">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="acb11-151">이러한 키는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-151">These keys can't be used together.</span></span>
  - <span data-ttu-id="acb11-152">`ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-152">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="acb11-153">`RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-153">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="acb11-154">`MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-154">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="acb11-155">`RequiredVersion` 는 Windows PowerShell 5.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-155">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="acb11-156">`MaximumVersion` 는 Windows PowerShell 5.1에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-156">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="acb11-157">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-157">For example:</span></span>

<span data-ttu-id="acb11-158">`AzureRM.Netcore`(버전 `0.12.0` 이상)이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-158">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="acb11-159">`AzureRM.Netcore`(버전 **만** `0.12.0` )이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-159">Require that `AzureRM.Netcore` (**only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="acb11-160">`AzureRM.Netcore`(버전 `0.12.0` 이상)이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-160">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="acb11-161">및의 모든 버전을 `AzureRM.Netcore` `PowerShellGet` 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-161">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="acb11-162">키를 사용 하는 경우 `RequiredVersion` 버전 문자열이 필요한 버전 문자열과 정확 하 게 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-162">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="acb11-163">**0.12** 는 **0.12.0** 와 정확히 일치 하지 않기 때문에 다음 예제는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-163">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="acb11-164">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="acb11-164">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="acb11-165">스크립트에 필요한 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-165">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="acb11-166">유효한 값은 PowerShell Core에 대 한 **Core** 및 Windows Powershell의 **데스크톱** 입니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-166">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="acb11-167">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-167">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="acb11-168">-ShellId</span><span class="sxs-lookup"><span data-stu-id="acb11-168">-ShellId</span></span>

<span data-ttu-id="acb11-169">스크립트에 필요한 셸을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-169">Specifies the shell that the script requires.</span></span> <span data-ttu-id="acb11-170">셸 ID를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-170">Enter the shell ID.</span></span> <span data-ttu-id="acb11-171">**ShellId** 매개 변수를 사용 하는 경우 **add-pssnapin** 매개 변수도 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-171">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="acb11-172">자동 변수를 쿼리하여 현재 **ShellId** 을 찾을 수 있습니다 `$ShellId` .</span><span class="sxs-lookup"><span data-stu-id="acb11-172">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="acb11-173">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-173">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="acb11-174">이 매개 변수는 더 이상 사용 되지 않는 미니 셸에서 사용 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-174">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="acb11-175">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="acb11-175">-RunAsAdministrator</span></span>

<span data-ttu-id="acb11-176">이 스위치 매개 변수는 문에 추가 될 때 스크립트를 실행 하는 `#Requires` PowerShell 세션을 관리자 권한으로 시작 해야 함을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-176">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="acb11-177">**RunAsAdministrator** 매개 변수는 Windows 이외의 운영 체제에서 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-177">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="acb11-178">**RunAsAdministrator** 매개 변수는 PowerShell 4.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-178">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="acb11-179">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-179">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="acb11-180">예</span><span class="sxs-lookup"><span data-stu-id="acb11-180">Examples</span></span>

<span data-ttu-id="acb11-181">다음 스크립트에는 두 개의 `#Requires` 문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-181">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="acb11-182">두 문에 지정 된 요구 사항이 충족 되지 않으면 스크립트가 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-182">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="acb11-183">각 `#Requires` 문은 줄의 첫 번째 항목 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acb11-183">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="acb11-184">참조</span><span class="sxs-lookup"><span data-stu-id="acb11-184">See also</span></span>

[<span data-ttu-id="acb11-185">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="acb11-185">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="acb11-186">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="acb11-186">about_Language_Keywords</span></span>](about_Language_Keywords.md)
