---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 모듈 가져오기
ms.openlocfilehash: 78806f9fcfcdd0effa1599c46bfeecddb507722a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212002"
---
# <span data-ttu-id="b2bc8-103">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-103">Import-Module</span></span>

## <span data-ttu-id="b2bc8-104">개요</span><span class="sxs-lookup"><span data-stu-id="b2bc8-104">SYNOPSIS</span></span>
<span data-ttu-id="b2bc8-105">현재 세션에 모듈을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-105">Adds modules to the current session.</span></span>

## <span data-ttu-id="b2bc8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2bc8-106">SYNTAX</span></span>

### <span data-ttu-id="b2bc8-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="b2bc8-107">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="b2bc8-108">PSSession</span><span class="sxs-lookup"><span data-stu-id="b2bc8-108">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="b2bc8-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="b2bc8-109">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b2bc8-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b2bc8-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="b2bc8-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="b2bc8-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="b2bc8-112">어셈블리</span><span class="sxs-lookup"><span data-stu-id="b2bc8-112">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber] [-Scope <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b2bc8-113">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="b2bc8-113">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru] [-AsCustomObject]
 [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

## <span data-ttu-id="b2bc8-114">설명</span><span class="sxs-lookup"><span data-stu-id="b2bc8-114">DESCRIPTION</span></span>

<span data-ttu-id="b2bc8-115">`Import-Module`Cmdlet은 현재 세션에 하나 이상의 모듈을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-115">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="b2bc8-116">PowerShell 3.0부터 모듈의 명령이 나 공급자를 사용 하면 설치 된 모듈을 자동으로 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-116">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="b2bc8-117">그러나 여전히 `Import-Module` 명령을 사용 하 여 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-117">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="b2bc8-118">기본 설정 변수를 사용 하 여 자동 모듈 가져오기를 사용 하지 않도록 설정할 수 있습니다 `$PSModuleAutoloadingPreference` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-118">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="b2bc8-119">변수에 대 한 자세한 내용은 `$PSModuleAutoloadingPreference` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-119">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="b2bc8-120">모듈은 PowerShell에서 사용할 수 있는 멤버를 포함 하는 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-120">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="b2bc8-121">멤버에는 cmdlet, 공급자, 스크립트, 함수, 변수, 기타 도구 및 파일이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-121">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="b2bc8-122">모듈을 가져온 후 세션에서 해당 모듈 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-122">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="b2bc8-123">모듈에 대 한 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-123">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="b2bc8-124">기본적으로 `Import-Module` 은 모듈이 내보내는 모든 멤버를 가져오지만 **Alias** , **Function** , **Cmdlet** 및 **Variable** 매개 변수를 사용 하 여 가져올 멤버를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-124">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias** , **Function** , **Cmdlet** , and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="b2bc8-125">**NoClobber** 매개 변수는 `Import-Module` 현재 세션의 멤버와 이름이 같은 멤버를 가져오지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-125">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="b2bc8-126">`Import-Module` 현재 세션에만 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-126">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="b2bc8-127">모든 새 세션으로 모듈을 가져오려면 `Import-Module` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-127">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="b2bc8-128">프로필에 대한 자세한 내용은 [about_Profiles](About/about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-128">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="b2bc8-129">원격 컴퓨터에서 **PSSession** 을 만들어 PowerShell 원격을 사용 하도록 설정한 원격 Windows 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-129">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="b2bc8-130">그런 다음의 **PSSession** 매개 변수를 사용 `Import-Module` 하 여 원격 컴퓨터에 설치 된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-130">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="b2bc8-131">이제 현재 세션에서 가져온 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-131">You can now use the imported commands in the current session.</span></span> <span data-ttu-id="b2bc8-132">명령은 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-132">The commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="b2bc8-133">Windows PowerShell 3.0부터를 사용 하 여 cmdlet `Import-Module` 이 CDXML (Cmdlet 정의 XML) 파일에 정의 되어 있는 CIM (CIM(Common Information Model)) 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="b2bc8-134">이 기능을 사용하면 C++로 작성된 코드 어셈블리와 같은 비관리 코드 어셈블리에 구현된 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-134">This feature allows you to use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="b2bc8-135">Windows 운영 체제를 실행 하지 않는 컴퓨터를 포함 하 여 PowerShell 원격을 사용 하지 않는 원격 컴퓨터의 경우의 **CIMSession** 매개 변수를 사용 `Import-Module` 하 여 원격 컴퓨터에서 CIM 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-135">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="b2bc8-136">가져온 명령은 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-136">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="b2bc8-137">**CIMSession** 은 원격 컴퓨터의 WMI(WINDOWS MANAGEMENT INSTRUMENTATION) (WMI)에 대 한 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-137">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="b2bc8-138">예제</span><span class="sxs-lookup"><span data-stu-id="b2bc8-138">EXAMPLES</span></span>

### <span data-ttu-id="b2bc8-139">예제 1: 모듈의 멤버를 현재 세션으로 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-139">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="b2bc8-140">이 예제에서는 **Psdiagnostics** 모듈의 멤버를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-140">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="b2bc8-141">예제 2: 모듈 경로로 지정 된 모든 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-141">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="b2bc8-142">이 예에서는 환경 변수로 지정 된 경로에서 사용 가능한 모든 모듈을 `$env:PSModulePath` 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-142">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="b2bc8-143">예제 3: 여러 모듈의 멤버를 현재 세션으로 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-143">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="b2bc8-144">이 예제에서는 **Psdiagnostics** 및 **Dism** 모듈의 멤버를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-144">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="b2bc8-145">`Get-Module`Cmdlet은 **Psdiagnostics** 및 **Dism** 모듈을 가져오고 개체를 변수에 저장 합니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-145">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="b2bc8-146">**ListAvailable** 매개 변수는 아직 세션으로 가져오지 않은 모듈을 가져오는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-146">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="b2bc8-147">의 **Moduleinfo** 매개 변수를 `Import-Module` 사용 하 여 모듈을 현재 세션으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-147">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="b2bc8-148">예제 4: 경로로 지정 된 모든 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-148">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="b2bc8-149">이 예에서는 명시적 경로를 사용 하 여 가져올 모듈을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-149">This example uses an explicit path to identify the module to import.</span></span>

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

<span data-ttu-id="b2bc8-150">**Verbose** 매개 변수를 사용 하면 `Import-Module` 에서 모듈을 로드할 때 진행률을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-150">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="b2bc8-151">**Verbose** , **PassThru** 또는 **AsCustomObject** 매개 변수를 사용 하지 않으면에서 `Import-Module` 모듈을 가져올 때 출력이 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-151">Without the **Verbose** , **PassThru** , or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="b2bc8-152">예 5: 세션으로 가져온 모듈 멤버 제한</span><span class="sxs-lookup"><span data-stu-id="b2bc8-152">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="b2bc8-153">이 예에서는 세션으로 가져오는 모듈 멤버와 세션에 대 한이 명령의 영향을 제한 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-153">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="b2bc8-154">**함수** 매개 변수는 모듈에서 가져온 멤버를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-154">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="b2bc8-155">**별칭** , **변수** 및 **Cmdlet** 매개 변수를 사용 하 여 모듈이 가져오는 다른 멤버를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-155">You can also use the **Alias** , **Variable** , and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="b2bc8-156">`Get-Module`Cmdlet은 **psdiagnostics** 모듈을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-156">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="b2bc8-157">**ExportedCmdlets** 속성은 모듈이 내보내는 모든 cmdlet을 나열 하지만 모두 가져오지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-157">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

<span data-ttu-id="b2bc8-158">Cmdlet의 **Module** 매개 변수를 사용 하면 `Get-Command` **psdiagnostics** 모듈에서 가져온 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-158">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="b2bc8-159">결과는 `Disable-PSTrace` 및 cmdlet만 가져왔는지 확인 합니다 `Enable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-159">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="b2bc8-160">예제 6: 모듈의 멤버를 가져오고 접두사 추가</span><span class="sxs-lookup"><span data-stu-id="b2bc8-160">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="b2bc8-161">이 예제에서는 **Psdiagnostics** 모듈을 현재 세션으로 가져오고, 멤버 이름에 접두사를 추가한 다음, 접두사가 있는 멤버 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-161">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="b2bc8-162">의 **prefix** 매개 변수는 `Import-Module` 모듈에서 가져온 모든 멤버에 **x** 접두사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-162">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="b2bc8-163">접두사는 현재 세션의 멤버에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-163">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="b2bc8-164">모듈을 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-164">It does not change the module.</span></span> <span data-ttu-id="b2bc8-165">**PassThru** 매개 변수는 가져온 모듈을 나타내는 module 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-165">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

<span data-ttu-id="b2bc8-166">`Get-Command` 모듈에서 가져온 멤버를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-166">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="b2bc8-167">출력에는 모듈 멤버에 접두사가 올바르게 추가된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-167">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="b2bc8-168">예제 7: 사용자 지정 개체 가져오기 및 사용</span><span class="sxs-lookup"><span data-stu-id="b2bc8-168">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="b2bc8-169">이 예제에서는 **import-module** 에서 반환 된 사용자 지정 개체를 가져오고 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-169">This example demonstrates how to get and use the custom object returned by **Import-Module** .</span></span>

<span data-ttu-id="b2bc8-170">사용자 지정 개체에는 가져온 각각의 모듈 멤버를 나타내는 합성 멤버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-170">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="b2bc8-171">예를 들어 모듈의 함수와 cmdlet은 사용자 지정 개체의 스크립트 메서드로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-171">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="b2bc8-172">사용자 지정 개체는 스크립팅에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-172">Custom objects are useful in scripting.</span></span> <span data-ttu-id="b2bc8-173">또한 가져온 몇몇 개체의 이름이 같은 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-173">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="b2bc8-174">개체의 스크립트 메서드를 사용하는 것은 모듈 이름을 포함하여 가져온 멤버의 정규화된 이름을 지정하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-174">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="b2bc8-175">**AsCustomObject** 매개 변수는 스크립트 모듈을 가져오는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-175">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="b2bc8-176">사용 `Get-Module` 가능한 모듈 중 스크립트 모듈을 확인 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-176">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

<span data-ttu-id="b2bc8-177">**AsCustomObject** 매개 변수를 사용 하 여 사용자 지정 개체를 요청 하 고 **PassThru** 매개 변수를 사용 하 여 개체를 반환 하는 **캘린더 표시** 스크립트 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-177">The **Show-Calendar** script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="b2bc8-178">결과 사용자 지정 개체는 변수에 저장 됩니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-178">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="b2bc8-179">`$a`변수는 `Get-Member` 저장 된 개체의 속성 및 메서드를 표시 하기 위해 cmdlet으로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-179">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="b2bc8-180">출력에는 **일정 표시** 스크립트 메서드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-180">The output shows a **Show-Calendar** script method.</span></span>

<span data-ttu-id="b2bc8-181">**표시 일정** 스크립트 메서드를 호출 하려면 이름에 하이픈이 포함 되어 있으므로 메서드 이름을 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-181">To call the **Show-Calendar** script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="b2bc8-182">예 8: 모듈을 동일한 세션으로 다시 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-182">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="b2bc8-183">이 예제에서는 **Force** `Import-Module` 모듈을 동일한 세션으로 다시 가져오는 때의 Force 매개 변수를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-183">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="b2bc8-184">**Force** 매개 변수는 로드 된 모듈을 제거한 다음 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-184">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="b2bc8-185">첫 번째 명령은 **Psdiagnostics** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-185">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="b2bc8-186">두 번째 명령은 모듈을 다시 가져오는데, 이번에는 **Prefix** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-186">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="b2bc8-187">**Force** 매개 변수를 사용 하지 않으면 세션에 각 **psdiagnostics** cmdlet의 복사본 두 개가 포함 됩니다. 하나에는 표준 이름과 접두사가 붙은 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-187">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="b2bc8-188">예제 9: 가져온 명령에 의해 숨겨진 명령 실행</span><span class="sxs-lookup"><span data-stu-id="b2bc8-188">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="b2bc8-189">이 예제에서는 가져온 명령에서 숨긴 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-189">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="b2bc8-190">**Testmodule** 모듈에는 연도 `Get-Date` 와 날짜를 반환 하는 라는 함수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-190">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

<span data-ttu-id="b2bc8-191">첫 번째 `Get-Date` cmdlet은 현재 날짜를 사용 하 여 **DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-191">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="b2bc8-192">**Testmodule** 모듈을 가져온 후는 연도의 `Get-Date` 연도와 일자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-192">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="b2bc8-193">의 **all** 매개 변수를 사용 하 여 `Get-Command` `Get-Date` 세션의 모든 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-193">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="b2bc8-194">결과에는 세션에 두 개의 `Get-Date` 명령, 즉 **testmodule** 모듈의 함수 및 **Microsoft PowerShell** 모듈의 cmdlet이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-194">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="b2bc8-195">함수는 cmdlet 보다 우선 하므로 `Get-Date` cmdlet 대신 **testmodule** 모듈의 함수를 실행 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-195">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="b2bc8-196">원래 버전의를 실행 하려면 `Get-Date` 모듈 이름으로 명령 이름을 정규화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-196">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="b2bc8-197">PowerShell의 명령 우선 순위에 대 한 자세한 내용은 [about_Command_Precedence](about/about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-197">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="b2bc8-198">예 10: 모듈의 최소 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-198">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="b2bc8-199">이 예제에서는 **PowerShellGet** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-199">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="b2bc8-200">의 **MinimumVersion** 매개 변수를 사용 하 여 `Import-Module` 버전 2.0.0 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-200">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="b2bc8-201">또한 **RequiredVersion** 매개 변수를 사용 하 여 모듈의 특정 버전을 가져오거나 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 `#Requires` 스크립트에서 모듈의 특정 버전을 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-201">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="b2bc8-202">예 11: 정규화 된 이름을 사용 하 여 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-202">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="b2bc8-203">이 예제에서는 FullyQualifiedName를 사용 하 여 모듈의 특정 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-203">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### <span data-ttu-id="b2bc8-204">예 12: 정규화 된 경로를 사용 하 여 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-204">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="b2bc8-205">이 예에서는 정규화 된 경로를 사용 하 여 모듈의 특정 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-205">This example imports a specific version of a module using the fully qualified path.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### <span data-ttu-id="b2bc8-206">예제 13: 원격 컴퓨터에서 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2bc8-206">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="b2bc8-207">이 예제에서는 cmdlet을 사용 하 여 `Import-Module` 원격 컴퓨터에서 모듈을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-207">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="b2bc8-208">이 명령은 PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-208">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="b2bc8-209">다른 세션에서 모듈을 가져오면 현재 세션에서 해당 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-209">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="b2bc8-210">그러나 cmdlet을 사용 하는 명령은 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-210">However, commands that use the cmdlets run in the remote session.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

<span data-ttu-id="b2bc8-211">`New-PSSession` Server01 컴퓨터에 대 한 원격 세션 ( **PSSession** )을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-211">`New-PSSession` creates a remote session ( **PSSession** ) to the Server01 computer.</span></span> <span data-ttu-id="b2bc8-212">**PSSession** 은 변수에 저장 됩니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-212">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="b2bc8-213">`Get-Module` **PSSession** 매개 변수를 사용 하 여를 실행 하는 경우 **netsecurity** 모듈이 설치 되어 원격 컴퓨터에 사용 가능 하다는 것을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-213">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="b2bc8-214">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Module` 원격 세션에서 명령을 실행 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-214">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="b2bc8-215">예: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="b2bc8-215">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="b2bc8-216">`Import-Module` **PSSession** 매개 변수를 사용 하 여를 실행 하면 원격 컴퓨터에서 현재 세션으로 **netsecurity** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-216">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="b2bc8-217">`Get-Command`Cmdlet은 **netsecurity** 모듈의 **get** 및 include **방화벽** 으로 시작 하는 명령을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-217">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="b2bc8-218">출력은 모듈과 해당 cmdlet을 현재 세션으로 가져왔는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-218">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="b2bc8-219">그런 다음 `Get-NetFirewallRule` cmdlet은 Server01 컴퓨터에 Windows 원격 관리 방화벽 규칙을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-219">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="b2bc8-220">이는 cmdlet을 사용 하 여 `Invoke-Command` `Get-NetFirewallRule` 원격 세션에서 실행 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-220">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="b2bc8-221">예 14: Windows 운영 체제를 사용 하지 않고 원격 컴퓨터의 저장소 관리</span><span class="sxs-lookup"><span data-stu-id="b2bc8-221">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="b2bc8-222">이 예에서는 컴퓨터의 관리자가 모듈 검색 WMI 공급자를 설치 하 여 공급자 용으로 설계 된 CIM 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-222">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="b2bc8-223">`New-CimSession`Cmdlet은 여 rsdgf03 이라는 원격 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-223">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="b2bc8-224">세션은 원격 컴퓨터의 WMI 서비스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-224">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="b2bc8-225">CIM 세션은 변수에 저장 됩니다 `$cs` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-225">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="b2bc8-226">`Import-Module` 는의 **CimSession** 를 사용 하 여 `$cs` 여 rsdgf03 컴퓨터에서 **저장소** CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-226">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="b2bc8-227">`Get-Command`Cmdlet은 `Get-Disk` **저장소** 모듈의 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-227">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="b2bc8-228">CIM 모듈을 로컬 세션으로 가져오면 PowerShell은 각 명령의 CDXML 파일을 로컬 세션의 함수로 표시 되는 PowerShell 스크립트로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-228">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="b2bc8-229">`Get-Disk`는 로컬 세션에서 형식화 되었지만 cmdlet은 해당 파일을 가져온 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-229">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="b2bc8-230">이 명령은 원격 컴퓨터에서 로컬 세션으로 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-230">The command returns objects from the remote computer to the local session.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## <span data-ttu-id="b2bc8-231">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2bc8-231">PARAMETERS</span></span>

### <span data-ttu-id="b2bc8-232">-별칭</span><span class="sxs-lookup"><span data-stu-id="b2bc8-232">-Alias</span></span>

<span data-ttu-id="b2bc8-233">이 cmdlet이 모듈에서 현재 세션으로 가져오는 별칭을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-233">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="b2bc8-234">쉼표로 구분된 별칭 목록을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-234">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="b2bc8-235">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-235">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b2bc8-236">모듈을 가져올 때 선택된 별칭을 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-236">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="b2bc8-237">이 매개 변수를 사용하면 내보내는 별칭 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-237">This parameter lets you select from among the exported aliases.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b2bc8-238">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="b2bc8-238">-ArgumentList</span></span>

<span data-ttu-id="b2bc8-239">명령 중에 스크립트 모듈로 전달 되는 인수 또는 매개 변수 값의 배열을 지정 합니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-239">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="b2bc8-240">이 매개 변수는 스크립트 모듈을 가져오는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-240">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="b2bc8-241">또한 **인수** 에 따라 **argumentlist** 매개 변수를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-241">You can also refer to the **ArgumentList** parameter by its alias, **args** .</span></span> <span data-ttu-id="b2bc8-242">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-242">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-243">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="b2bc8-243">-AsCustomObject</span></span>

<span data-ttu-id="b2bc8-244">이 cmdlet은 가져온 모듈 멤버를 나타내는 멤버가 있는 사용자 지정 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-244">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="b2bc8-245">이 매개 변수는 스크립트 모듈에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-245">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="b2bc8-246">**AsCustomObject** 매개 변수를 사용 하는 경우는 `Import-Module` 모듈 멤버를 세션으로 가져온 다음 **Psmoduleinfo** 개체 대신 **PSCustomObject** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-246">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="b2bc8-247">사용자 지정 개체를 변수에 저장하고 점 표기법을 사용하여 멤버를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-247">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-248">-어셈블리</span><span class="sxs-lookup"><span data-stu-id="b2bc8-248">-Assembly</span></span>

<span data-ttu-id="b2bc8-249">어셈블리 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-249">Specifies an array of assembly objects.</span></span> <span data-ttu-id="b2bc8-250">이 cmdlet은 지정 된 어셈블리 개체에 구현 된 cmdlet 및 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-250">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="b2bc8-251">어셈블리 개체가 포함된 변수나 어셈블리 개체를 만드는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-251">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="b2bc8-252">어셈블리 개체를로 파이프 할 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-252">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="b2bc8-253">이 매개 변수를 사용하면 지정된 어셈블리에서 구현한 cmdlet과 공급자만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-253">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="b2bc8-254">모듈에 다른 파일이 포함 되어 있으면 해당 파일을 가져오지 않으며 모듈의 중요 한 멤버가 누락 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-254">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="b2bc8-255">모듈을 디버깅 하 고 테스트 하는 데이 매개 변수를 사용 하거나 모듈 작성자가 사용 하도록 지시 하는 경우이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-255">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-256">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="b2bc8-256">-CimNamespace</span></span>

<span data-ttu-id="b2bc8-257">CIM 모듈을 표시하는 대체 CIM 공급자의 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-257">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="b2bc8-258">기본값은 모듈 검색 WMI 공급자의 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-258">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="b2bc8-259">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-259">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="b2bc8-260">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-261">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="b2bc8-261">-CimResourceUri</span></span>

<span data-ttu-id="b2bc8-262">CIM 모듈의 대체 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-262">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="b2bc8-263">기본값은 원격 컴퓨터의 모듈 검색 WMI 공급자에 대 한 리소스 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-263">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="b2bc8-264">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-264">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="b2bc8-265">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-265">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-266">-CimSession</span><span class="sxs-lookup"><span data-stu-id="b2bc8-266">-CimSession</span></span>

<span data-ttu-id="b2bc8-267">원격 컴퓨터에서 CIM 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-267">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="b2bc8-268">Cim 세션을 포함 하는 변수 또는 CIM 세션을 가져오는 명령 (예: [CimSession](../CimCmdlets/Get-CimSession.md) 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-268">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="b2bc8-269">`Import-Module` CIM 세션 연결을 사용 하 여 원격 컴퓨터에서 현재 세션으로 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-269">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="b2bc8-270">현재 세션에서 가져온 모듈의 명령을 사용 하면 명령이 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-270">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="b2bc8-271">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 Windows 컴퓨터에서 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-271">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="b2bc8-272">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-273">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2bc8-273">-Cmdlet</span></span>

<span data-ttu-id="b2bc8-274">이 cmdlet이 모듈에서 현재 세션으로 가져오는 cmdlet의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-274">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="b2bc8-275">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b2bc8-276">모듈을 가져올 때 선택된 cmdlet을 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-276">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="b2bc8-277">이 매개 변수를 사용하면 내보내는 cmdlet 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-277">This parameter lets you select from among the exported cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b2bc8-278">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="b2bc8-278">-DisableNameChecking</span></span>

<span data-ttu-id="b2bc8-279">이 cmdlet은 이름에 승인 되지 않은 동사 나 금지 된 문자가 포함 된 cmdlet 또는 함수를 가져올 때 경고 메시지를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-279">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="b2bc8-280">기본적으로 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 PowerShell에서 다음과 같은 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-280">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="b2bc8-281">경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-281">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="b2bc8-282">자세한 내용을 보려면 Verbose 매개 변수를 사용하거나 승인된 동사 목록을 보려면 Get-Verb를 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-282">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="b2bc8-283">이 메시지는 경고일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-283">This message is only a warning.</span></span> <span data-ttu-id="b2bc8-284">비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-284">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="b2bc8-285">메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-285">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-286">-Force</span><span class="sxs-lookup"><span data-stu-id="b2bc8-286">-Force</span></span>

<span data-ttu-id="b2bc8-287">이 매개 변수를 통해 모듈을 로드 하거나 현재 모듈 위에 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-287">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-288">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b2bc8-288">-FullyQualifiedName</span></span>

<span data-ttu-id="b2bc8-289">모듈의 정규화 된 이름을 해시 테이블로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-289">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="b2bc8-290">값은 문자열과 해시 테이블의 조합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-290">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="b2bc8-291">해시 테이블에는 다음과 같은 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-291">The hash table has the following keys.</span></span>

- <span data-ttu-id="b2bc8-292">`ModuleName` - **필수** 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-292">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="b2bc8-293">`GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-293">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="b2bc8-294">또한 아래 세 키 중 하나를 지정 **해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-294">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="b2bc8-295">이러한 키는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-295">These keys can't be used together.</span></span>
  - <span data-ttu-id="b2bc8-296">`ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-296">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="b2bc8-297">`RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-297">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="b2bc8-298">`MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-298">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-299">-함수</span><span class="sxs-lookup"><span data-stu-id="b2bc8-299">-Function</span></span>

<span data-ttu-id="b2bc8-300">이 cmdlet이 모듈에서 현재 세션으로 가져오는 함수 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-300">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="b2bc8-301">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-301">Wildcard characters are permitted.</span></span> <span data-ttu-id="b2bc8-302">모듈을 가져올 때 선택된 함수를 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-302">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="b2bc8-303">이 매개 변수를 사용하면 내보내는 함수 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-303">This parameter lets you select from among the exported functions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b2bc8-304">-전역</span><span class="sxs-lookup"><span data-stu-id="b2bc8-304">-Global</span></span>

<span data-ttu-id="b2bc8-305">이 cmdlet은 모듈을 전역 세션 상태로 가져오므로 세션의 모든 명령에서 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-305">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="b2bc8-306">기본적으로 `Import-Module` 명령 프롬프트, 스크립트 파일 또는 scriptblock에서 cmdlet을 호출 하면 모든 명령을 전역 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-306">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="b2bc8-307">다른 모듈에서 호출 되는 경우 `Import-Module` cmdlet은 중첩 모듈의 명령을 포함 하 여 모듈의 명령을 호출 하는 모듈의 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-307">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="b2bc8-308">`Import-Module`모듈 내에서를 호출 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-308">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="b2bc8-309">대신, 부모 모듈의 매니페스트에서 대상 모듈을 중첩 모듈로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-309">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="b2bc8-310">중첩 모듈을 선언 하면 종속성의 검색 기능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-310">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="b2bc8-311">**Global** 매개 변수는 **Global** 값을 사용하는 **Scope** 매개 변수와 동일한 결과를 낳습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-311">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global** .</span></span>

<span data-ttu-id="b2bc8-312">모듈에서 내보내는 명령을 제한 하려면 `Export-ModuleMember` 스크립트 모듈의 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-312">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-313">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b2bc8-313">-MaximumVersion</span></span>

<span data-ttu-id="b2bc8-314">최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-314">Specifies a maximum version.</span></span> <span data-ttu-id="b2bc8-315">이 cmdlet은 지정 된 값 보다 작거나 같은 버전의 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-315">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="b2bc8-316">버전이 한정 되지 않은 경우는 `Import-Module` 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-316">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-317">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b2bc8-317">-MinimumVersion</span></span>

<span data-ttu-id="b2bc8-318">최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-318">Specifies a minimum version.</span></span> <span data-ttu-id="b2bc8-319">이 cmdlet은 지정 된 값 보다 크거나 같은 버전의 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-319">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="b2bc8-320">**MinimumVersion** 매개 변수 이름 또는 그 별칭인 **Version** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-320">Use the **MinimumVersion** parameter name or its alias, **Version** .</span></span> <span data-ttu-id="b2bc8-321">버전이 한정 되지 않은 경우는 `Import-Module` 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-321">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="b2bc8-322">정확한 버전을 지정하려면 **RequiredVersion** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-322">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="b2bc8-323">**#Requires** 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 스크립트에서 모듈의 특정 버전을 요구할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-323">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="b2bc8-324">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-325">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="b2bc8-325">-ModuleInfo</span></span>

<span data-ttu-id="b2bc8-326">가져올 모듈 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-326">Specifies an array of module objects to import.</span></span> <span data-ttu-id="b2bc8-327">모듈 개체를 포함 하는 변수를 입력 하거나 모듈 개체를 가져오는 명령 (예:)을 입력 `Get-Module -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-327">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="b2bc8-328">모듈 개체를로 파이프 할 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-328">You can also pipe module objects to `Import-Module`.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-329">-Name</span><span class="sxs-lookup"><span data-stu-id="b2bc8-329">-Name</span></span>

<span data-ttu-id="b2bc8-330">가져올 모듈의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-330">Specifies the names of the modules to import.</span></span> <span data-ttu-id="b2bc8-331">모듈 이름 또는 모듈의 파일 이름 (예: `.psd1` ,, `.psm1` `.dll` 또는 파일)을 입력 합니다 `.ps1` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-331">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="b2bc8-332">파일 경로는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-332">File paths are optional.</span></span> <span data-ttu-id="b2bc8-333">와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-333">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="b2bc8-334">모듈 이름 및 파일 이름을로 파이프 할 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-334">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="b2bc8-335">경로를 생략 하면는 `Import-Module` 환경 변수에 저장 된 경로에서 모듈을 찾습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-335">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="b2bc8-336">가능하면 항상 모듈 이름만 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-336">Specify only the module name whenever possible.</span></span> <span data-ttu-id="b2bc8-337">파일 이름을 지정하는 경우 해당 파일에 구현된 멤버만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-337">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="b2bc8-338">모듈에 다른 파일이 포함 되어 있으면 해당 파일을 가져오지 않으며 모듈의 중요 한 멤버가 누락 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-338">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b2bc8-339">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="b2bc8-339">-NoClobber</span></span>

<span data-ttu-id="b2bc8-340">현재 세션에 있는 기존 명령과 이름이 동일한 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-340">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="b2bc8-341">기본적으로는 `Import-Module` 내보낸 모든 모듈 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-341">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="b2bc8-342">이름이 같은 명령은 세션의 명령을 숨기 거 나 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-342">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="b2bc8-343">세션에서 명령 이름 충돌을 방지하려면 **Prefix** 또는 **NoClobber** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-343">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="b2bc8-344">이름 충돌 및 명령 우선 순위에 대한 자세한 내용은 [about_Modules](about/about_Modules.md) 및 [about_Command_Precedence](about/about_Command_Precedence.md)의 "모듈 및 이름 충돌"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-344">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="b2bc8-345">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-345">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-346">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b2bc8-346">-PassThru</span></span>

<span data-ttu-id="b2bc8-347">작업 중인 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-347">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="b2bc8-348">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-348">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-349">-접두사</span><span class="sxs-lookup"><span data-stu-id="b2bc8-349">-Prefix</span></span>

<span data-ttu-id="b2bc8-350">이 cmdlet이 가져온 모듈 멤버의 이름에 있는 명사에 추가 하는 접두사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-350">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="b2bc8-351">세션에 있는 서로 다른 멤버의 이름이 동일한 경우 발생할 수 있는 이름 충돌을 방지하려면 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-351">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="b2bc8-352">이 매개 변수는 모듈을 변경 하지 않으며 모듈에서 자체적으로 사용 하기 위해 가져오는 파일에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-352">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="b2bc8-353">이를 중첩 모듈 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-353">These are known as nested modules.</span></span> <span data-ttu-id="b2bc8-354">이 cmdlet은 현재 세션에 있는 멤버의 이름에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-354">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="b2bc8-355">예를 들어, 접두사 UTC를 지정 하 고 cmdlet을 가져오면이 `Get-Date` cmdlet은 세션에서로 알려져 `Get-UTCDate` 있으며 원래 cmdlet과는 혼동 되지 않습니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-355">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="b2bc8-356">이 매개 변수 값은 기본 접두사를 지정하는 모듈의 **DefaultCommandPrefix** 속성보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-356">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-357">-PSSession</span><span class="sxs-lookup"><span data-stu-id="b2bc8-357">-PSSession</span></span>

<span data-ttu-id="b2bc8-358">이 cmdlet이 모듈을 현재 세션으로 가져오는 PowerShell 사용자 관리 세션 ( **PSSession** )을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-358">Specifies a PowerShell user-managed session ( **PSSession** ) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="b2bc8-359">**Pssession이** 포함 된 변수 또는 **pssession** 을 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-359">Enter a variable that contains a **PSSession** or a command that gets a **PSSession** , such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="b2bc8-360">다른 세션에서 현재 세션으로 모듈을 가져오면 로컬 모듈의 cmdlet을 사용할 때와 마찬가지로 현재 세션에서 해당 모듈의 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-360">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="b2bc8-361">원격 cmdlet을 사용 하는 명령은 원격 세션에서 실행 되지만 원격 세부 정보는 PowerShell을 통해 백그라운드에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-361">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="b2bc8-362">이 매개 변수는 PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-362">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="b2bc8-363">Cmdlet을 사용 하 여 `Import-PSSession` 세션에서 특정 모듈을 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-363">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="b2bc8-364">`Import-Module` 다른 세션에서 PowerShell 핵심 모듈을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-364">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="b2bc8-365">PowerShell 핵심 모듈의 이름은 Microsoft. PowerShell로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-365">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="b2bc8-366">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-366">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-367">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b2bc8-367">-RequiredVersion</span></span>

<span data-ttu-id="b2bc8-368">이 cmdlet이 가져오는 모듈의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-368">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="b2bc8-369">버전이 설치 되어 있지 않으면에서 `Import-Module` 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-369">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="b2bc8-370">기본적으로는 `Import-Module` 버전 번호를 확인 하지 않고 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-370">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="b2bc8-371">최소 버전을 지정하려면 **MinimumVersion** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-371">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="b2bc8-372">**#Requires** 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 스크립트에서 모듈의 특정 버전을 요구할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-372">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="b2bc8-373">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-373">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="b2bc8-374">**RequiredVersion** 을 사용 하 여 기존 버전의 windows 운영 체제에 포함 된 모듈을 가져오는 스크립트는 이후 버전의 windows 운영 체제에서 자동으로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-374">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="b2bc8-375">이는 Windows 운영 체제의 이후 릴리스에서 PowerShell 모듈 버전 번호가 기존 버전의 Windows 운영 체제에서 모듈 버전 번호 보다 높기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-375">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-376">-범위</span><span class="sxs-lookup"><span data-stu-id="b2bc8-376">-Scope</span></span>

<span data-ttu-id="b2bc8-377">이 cmdlet이 모듈을 가져올 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-377">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="b2bc8-378">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-378">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b2bc8-379">**전역** .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-379">**Global** .</span></span> <span data-ttu-id="b2bc8-380">세션의 모든 명령에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-380">Available to all commands in the session.</span></span> <span data-ttu-id="b2bc8-381">**Global** 매개 변수를 사용하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-381">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="b2bc8-382">**로컬** .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-382">**Local** .</span></span> <span data-ttu-id="b2bc8-383">현재 범위에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-383">Available only in the current scope.</span></span>

<span data-ttu-id="b2bc8-384">기본적으로 `Import-Module` 명령 프롬프트, 스크립트 파일 또는 scriptblock에서 cmdlet을 호출 하면 모든 명령을 전역 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-384">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="b2bc8-385">**-Scope** 매개 변수를 **Local** 값과 함께 사용 하 여 모듈 콘텐츠를 스크립트 또는 scriptblock 범위로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-385">You can use the **-Scope** parameter with the value of **Local** to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="b2bc8-386">다른 모듈에서 호출 되는 경우 `Import-Module` cmdlet은 중첩 모듈의 명령을 포함 하 여 모듈의 명령을 호출자의 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-386">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="b2bc8-387">또는를 지정 하면 `-Scope Global` `-Global` 이 cmdlet이 모듈을 전역 세션 상태로 가져오므로 세션의 모든 명령에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-387">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="b2bc8-388">**Global** 매개 변수는 global 값을 사용 하는 **범위** 매개 변수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-388">The **Global** parameter is equivalent to the **Scope** parameter with a value of Global.</span></span>

<span data-ttu-id="b2bc8-389">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-389">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2bc8-390">-Variable</span><span class="sxs-lookup"><span data-stu-id="b2bc8-390">-Variable</span></span>

<span data-ttu-id="b2bc8-391">이 cmdlet이 모듈에서 현재 세션으로 가져오는 변수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-391">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="b2bc8-392">변수의 목록을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-392">Enter a list of variables.</span></span> <span data-ttu-id="b2bc8-393">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-393">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b2bc8-394">모듈을 가져올 때 선택된 변수를 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-394">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="b2bc8-395">이 매개 변수를 사용하면 내보내는 변수 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-395">This parameter lets you select from among the exported variables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b2bc8-396">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2bc8-396">CommonParameters</span></span>
<span data-ttu-id="b2bc8-397">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-397">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2bc8-398">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-398">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2bc8-399">입력</span><span class="sxs-lookup"><span data-stu-id="b2bc8-399">INPUTS</span></span>

### <span data-ttu-id="b2bc8-400">System.string, System.web.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-400">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="b2bc8-401">모듈 이름, 모듈 개체 또는 어셈블리 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-401">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="b2bc8-402">출력</span><span class="sxs-lookup"><span data-stu-id="b2bc8-402">OUTPUTS</span></span>

### <span data-ttu-id="b2bc8-403">None, PSCustomObject 또는. m i n. a p.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-403">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="b2bc8-404">기본적으로는 `Import-Module` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-404">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="b2bc8-405">**PassThru** 매개 변수를 지정 하는 경우 cmdlet은 모듈을 나타내는 **system.object** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-405">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="b2bc8-406">**AsCustomObject** 매개 변수를 지정 하면 **PSCustomObject** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-406">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="b2bc8-407">참고</span><span class="sxs-lookup"><span data-stu-id="b2bc8-407">NOTES</span></span>

- <span data-ttu-id="b2bc8-408">모듈을 가져오려면 모듈이 로컬 컴퓨터에 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-408">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="b2bc8-409">즉, 모듈 디렉터리를 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-409">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="b2bc8-410">자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-410">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="b2bc8-411">**PSSession** 및 **CIMSession** 매개 변수를 사용하여 원격 컴퓨터에 설치된 모듈을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-411">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="b2bc8-412">그러나 이러한 모듈의 cmdlet을 사용 하는 명령은 원격 컴퓨터의 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-412">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="b2bc8-413">이름과 형식이 같은 멤버를 세션에 가져오는 경우 PowerShell은 기본적으로 마지막으로 가져온 멤버를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-413">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="b2bc8-414">변수와 별칭은 바뀌고 원본에는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-414">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="b2bc8-415">함수, cmdlet 및 공급자는 단순히 새 멤버로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-415">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="b2bc8-416">스냅인, 모듈 또는 함수 경로의 이름으로 명령 이름을 정규화 하 여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-416">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="b2bc8-417">모듈에서 가져온 명령에 대 한 형식 지정 데이터를 업데이트 하려면 cmdlet을 사용 `Update-FormatData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-417">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="b2bc8-418">`Update-FormatData` 는 모듈에서 가져온 세션의 명령에 대 한 형식 지정 데이터도 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-418">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="b2bc8-419">모듈에 대 한 형식 지정 파일이 변경 되 면 `Update-FormatData` 명령을 실행 하 여 가져온 명령에 대 한 형식 지정 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-419">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="b2bc8-420">모듈을 다시 가져올 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-420">You don't need to import the module again.</span></span>

- <span data-ttu-id="b2bc8-421">Windows PowerShell 3.0 부터는 PowerShell과 함께 설치 되는 핵심 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-421">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="b2bc8-422">Windows PowerShell 2.0 및 이후 버전의 PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 ( **PSSnapins** )으로 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-422">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="b2bc8-423">예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-423">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="b2bc8-424">또한 cmdlet에서 시작한 것과 같은 원격 세션 `New-PSSession` 은 핵심 스냅인을 포함 하는 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-424">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="b2bc8-425">핵심 모듈과 함께 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-425">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="b2bc8-426">`Import-Module` 다른 세션에서 PowerShell 핵심 모듈을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-426">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="b2bc8-427">PowerShell 핵심 모듈의 이름은로 시작 `Microsoft.PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-427">The PowerShell Core modules have names that begin with `Microsoft.PowerShell`.</span></span>

- <span data-ttu-id="b2bc8-428">Windows PowerShell 2.0에서 **ExportedCmdlets** 및 **NestedModules** 속성 값과 같은 module 개체의 일부 속성 값은 모듈을 가져올 때까지 채워지지 않으며 **PassThru** 매개 변수가 반환 하는 module 개체에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-428">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported and were not available on the module object that the **PassThru** parameter returns.</span></span> <span data-ttu-id="b2bc8-429">Windows PowerShell 3.0에서는 모든 모듈 속성 값이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-429">In Windows PowerShell 3.0, all module property values are populated.</span></span>

- <span data-ttu-id="b2bc8-430">Windows PowerShell 3.0와 호환 되지 않는 혼합 모드 어셈블리를 포함 하는 모듈을 가져오려고 시도 하면에서 `Import-Module` 다음과 같은 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-430">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="b2bc8-431">Import-Module: 혼합 모드 어셈블리는 런타임의 버전 ' v 2.0.50727 '에 대해 빌드 되었으며 추가 구성 정보 없이 4.0 런타임에 로드 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-431">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="b2bc8-432">이 오류는 Windows PowerShell 2.0 용으로 설계 된 모듈에 관리 되는 코드와 관리 되지 않는 코드 (예: c + + 및 c #)가 모두 포함 된 어셈블리 인 혼합 모듈 어셈블리가 하나 이상 있는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-432">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly, that is, an assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="b2bc8-433">혼합 모드 어셈블리를 포함 하는 모듈을 가져오려면 다음 명령을 사용 하 여 Windows PowerShell 2.0을 시작한 후 명령을 다시 시도 하십시오 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b2bc8-433">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="b2bc8-434">CIM 세션 기능을 사용하려면 원격 컴퓨터에 WS-Management 원격 기능과 CIM(Common Information Model) 표준에 대한 Microsoft 구현인 WMI(Windows Management Instrumentation)가 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-434">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="b2bc8-435">컴퓨터에도 모듈 검색 WMI 공급자 또는 동일한 기본 기능을 갖춘 대체 CIM 공급자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-435">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="b2bc8-436">Windows 운영 체제를 실행 하지 않는 컴퓨터 및 PowerShell이 있는 Windows 컴퓨터에서 CIM 세션 기능을 사용할 수 있지만 PowerShell 원격을 사용 하도록 설정 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-436">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="b2bc8-437">CIM 매개 변수를 사용 하 여 로컬 컴퓨터를 포함 하 여 PowerShell 원격을 사용 하도록 설정한 컴퓨터에서 CIM 모듈을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-437">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="b2bc8-438">로컬 컴퓨터에서 CIM 세션을 만드는 경우 PowerShell은 WMI 대신 DCOM을 사용 하 여 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-438">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="b2bc8-439">기본적으로는 `Import-Module` 하위 범위에서 호출 된 경우에도 전역 범위에서 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-439">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="b2bc8-440">최상위 범위 및 모든 하위 범위는 모듈의 내보낸 요소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-440">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="b2bc8-441">하위 항목 범위에서 `-Scope Local` 는 해당 범위 및 모든 하위 항목 범위로 가져오기를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-441">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="b2bc8-442">그러면 부모 범위에 가져온 멤버가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-442">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b2bc8-443">`Get-Module` 현재 세션에 로드 된 모든 모듈을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-443">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="b2bc8-444">여기에는 하위 항목 범위에서 로컬로 로드 된 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-444">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="b2bc8-445">`Get-Command -Module modulename`현재 범위에서 로드 된 멤버를 확인 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-445">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="b2bc8-446">모듈에 클래스 및 열거형 정의가 포함 된 경우에는 `using module` 스크립트 시작 부분에서를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-446">If the module includes class and enum definitions, use `using module` at the beginning of your script.</span></span> <span data-ttu-id="b2bc8-447">이를 통해 클래스 및 열거형 정의를 포함 하는 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-447">This import the scripts, including the class and enum definitions.</span></span> <span data-ttu-id="b2bc8-448">자세한 내용은 [about_Using](About/about_Using.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2bc8-448">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="b2bc8-449">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b2bc8-449">RELATED LINKS</span></span>

[<span data-ttu-id="b2bc8-450">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="b2bc8-450">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="b2bc8-451">Get-Module</span><span class="sxs-lookup"><span data-stu-id="b2bc8-451">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="b2bc8-452">New-Module</span><span class="sxs-lookup"><span data-stu-id="b2bc8-452">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="b2bc8-453">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="b2bc8-453">Remove-Module</span></span>](Remove-Module.md)
