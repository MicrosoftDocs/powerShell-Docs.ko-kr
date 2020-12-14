---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 모듈 가져오기
ms.openlocfilehash: 218a4cb447c85a7362efebe9b50a917703cccc35
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564448"
---
# <span data-ttu-id="1b525-102">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-102">Import-Module</span></span>

## <span data-ttu-id="1b525-103">개요</span><span class="sxs-lookup"><span data-stu-id="1b525-103">SYNOPSIS</span></span>
<span data-ttu-id="1b525-104">현재 세션에 모듈을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-104">Adds modules to the current session.</span></span>

## <span data-ttu-id="1b525-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b525-105">SYNTAX</span></span>

### <span data-ttu-id="1b525-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="1b525-106">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="1b525-107">PSSession</span><span class="sxs-lookup"><span data-stu-id="1b525-107">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="1b525-108">CimSession</span><span class="sxs-lookup"><span data-stu-id="1b525-108">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="1b525-109">UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="1b525-109">UseWindowsPowerShell</span></span>

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="1b525-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1b525-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="1b525-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="1b525-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="1b525-112">FullyQualifiedNameAndUseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="1b525-112">FullyQualifiedNameAndUseWindowsPowerShell</span></span>

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="1b525-113">어셈블리</span><span class="sxs-lookup"><span data-stu-id="1b525-113">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="1b525-114">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="1b525-114">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="1b525-115">설명</span><span class="sxs-lookup"><span data-stu-id="1b525-115">DESCRIPTION</span></span>

<span data-ttu-id="1b525-116">`Import-Module`Cmdlet은 현재 세션에 하나 이상의 모듈을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-116">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="1b525-117">PowerShell 3.0부터 모듈의 명령이 나 공급자를 사용 하면 설치 된 모듈을 자동으로 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-117">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="1b525-118">그러나 여전히 `Import-Module` 명령을 사용 하 여 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-118">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="1b525-119">기본 설정 변수를 사용 하 여 자동 모듈 가져오기를 사용 하지 않도록 설정할 수 있습니다 `$PSModuleAutoloadingPreference` .</span><span class="sxs-lookup"><span data-stu-id="1b525-119">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="1b525-120">변수에 대 한 자세한 내용은 `$PSModuleAutoloadingPreference` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-120">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="1b525-121">모듈은 PowerShell에서 사용할 수 있는 멤버를 포함 하는 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-121">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="1b525-122">멤버에는 cmdlet, 공급자, 스크립트, 함수, 변수, 기타 도구 및 파일이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-122">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="1b525-123">모듈을 가져온 후 세션에서 해당 모듈 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-123">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="1b525-124">모듈에 대 한 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-124">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="1b525-125">기본적으로 `Import-Module` 은 모듈이 내보내는 모든 멤버를 가져오지만 **Alias**, **Function**, **Cmdlet** 및 **Variable** 매개 변수를 사용 하 여 가져올 멤버를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-125">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias**, **Function**, **Cmdlet**, and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="1b525-126">**NoClobber** 매개 변수는 `Import-Module` 현재 세션의 멤버와 이름이 같은 멤버를 가져오지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-126">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="1b525-127">`Import-Module` 현재 세션에만 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-127">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="1b525-128">모든 새 세션으로 모듈을 가져오려면 `Import-Module` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-128">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="1b525-129">프로필에 대한 자세한 내용은 [about_Profiles](About/about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-129">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="1b525-130">원격 컴퓨터에서 **PSSession** 을 만들어 PowerShell 원격을 사용 하도록 설정한 원격 Windows 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-130">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="1b525-131">그런 다음의 **PSSession** 매개 변수를 사용 `Import-Module` 하 여 원격 컴퓨터에 설치 된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-131">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="1b525-132">현재 세션에서 가져온 명령을 사용 하면 명령이 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-132">When you use the imported commands in the current session the commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="1b525-133">Windows PowerShell 3.0부터를 사용 `Import-Module` 하 여 CIM (CIM(Common Information Model)) 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="1b525-134">CIM 모듈은 CDXML (Cmdlet 정의 XML) 파일에 cmdlet을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-134">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="1b525-135">이 기능을 사용 하면 c + +로 작성 된 코드 어셈블리와 같이 관리 되지 않는 코드 어셈블리에 구현 된 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-135">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="1b525-136">Windows 운영 체제를 실행 하지 않는 컴퓨터를 포함 하 여 PowerShell 원격을 사용 하지 않는 원격 컴퓨터의 경우의 **CIMSession** 매개 변수를 사용 `Import-Module` 하 여 원격 컴퓨터에서 CIM 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-136">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="1b525-137">가져온 명령은 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-137">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="1b525-138">**CIMSession** 은 원격 컴퓨터의 WMI(WINDOWS MANAGEMENT INSTRUMENTATION) (WMI)에 대 한 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-138">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="1b525-139">예제</span><span class="sxs-lookup"><span data-stu-id="1b525-139">EXAMPLES</span></span>

### <span data-ttu-id="1b525-140">예제 1: 모듈의 멤버를 현재 세션으로 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-140">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="1b525-141">이 예제에서는 **Psdiagnostics** 모듈의 멤버를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-141">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="1b525-142">예제 2: 모듈 경로로 지정 된 모든 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-142">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="1b525-143">이 예에서는 환경 변수로 지정 된 경로에서 사용 가능한 모든 모듈을 `$env:PSModulePath` 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-143">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="1b525-144">예제 3: 여러 모듈의 멤버를 현재 세션으로 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-144">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="1b525-145">이 예제에서는 **Psdiagnostics** 및 **Dism** 모듈의 멤버를 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-145">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="1b525-146">`Get-Module`Cmdlet은 **Psdiagnostics** 및 **Dism** 모듈을 가져오고 개체를 변수에 저장 합니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="1b525-146">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="1b525-147">**ListAvailable** 매개 변수는 아직 세션으로 가져오지 않은 모듈을 가져오는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-147">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="1b525-148">의 **Moduleinfo** 매개 변수를 `Import-Module` 사용 하 여 모듈을 현재 세션으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-148">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="1b525-149">예제 4: 경로로 지정 된 모든 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-149">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="1b525-150">이 예에서는 명시적 경로를 사용 하 여 가져올 모듈을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-150">This example uses an explicit path to identify the module to import.</span></span>

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

<span data-ttu-id="1b525-151">**Verbose** 매개 변수를 사용 하면 `Import-Module` 에서 모듈을 로드할 때 진행률을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-151">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="1b525-152">**Verbose**, **PassThru** 또는 **AsCustomObject** 매개 변수를 사용 하지 않으면에서 `Import-Module` 모듈을 가져올 때 출력이 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-152">Without the **Verbose**, **PassThru**, or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="1b525-153">예 5: 세션으로 가져온 모듈 멤버 제한</span><span class="sxs-lookup"><span data-stu-id="1b525-153">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="1b525-154">이 예에서는 세션으로 가져오는 모듈 멤버와 세션에 대 한이 명령의 영향을 제한 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-154">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="1b525-155">**함수** 매개 변수는 모듈에서 가져온 멤버를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-155">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="1b525-156">**별칭**, **변수** 및 **Cmdlet** 매개 변수를 사용 하 여 모듈이 가져오는 다른 멤버를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-156">You can also use the **Alias**, **Variable**, and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="1b525-157">`Get-Module`Cmdlet은 **psdiagnostics** 모듈을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-157">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="1b525-158">**ExportedCmdlets** 속성은 모듈이 내보내는 모든 cmdlet을 나열 하지만 모두 가져오지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-158">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

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

<span data-ttu-id="1b525-159">Cmdlet의 **Module** 매개 변수를 사용 하면 `Get-Command` **psdiagnostics** 모듈에서 가져온 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-159">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="1b525-160">결과는 `Disable-PSTrace` 및 cmdlet만 가져왔는지 확인 합니다 `Enable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="1b525-160">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="1b525-161">예제 6: 모듈의 멤버를 가져오고 접두사 추가</span><span class="sxs-lookup"><span data-stu-id="1b525-161">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="1b525-162">이 예제에서는 **Psdiagnostics** 모듈을 현재 세션으로 가져오고, 멤버 이름에 접두사를 추가한 다음, 접두사가 있는 멤버 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-162">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="1b525-163">의 **prefix** 매개 변수는 `Import-Module` 모듈에서 가져온 모든 멤버에 **x** 접두사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-163">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="1b525-164">접두사는 현재 세션의 멤버에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-164">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="1b525-165">모듈을 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-165">It does not change the module.</span></span> <span data-ttu-id="1b525-166">**PassThru** 매개 변수는 가져온 모듈을 나타내는 module 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-166">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

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

<span data-ttu-id="1b525-167">`Get-Command` 모듈에서 가져온 멤버를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-167">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="1b525-168">출력에는 모듈 멤버에 접두사가 올바르게 추가된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-168">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="1b525-169">예제 7: 사용자 지정 개체 가져오기 및 사용</span><span class="sxs-lookup"><span data-stu-id="1b525-169">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="1b525-170">이 예제에서는에서 반환 하는 사용자 지정 개체를 가져오고 사용 하는 방법을 보여 줍니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b525-170">This example demonstrates how to get and use the custom object returned by `Import-Module`.</span></span>

<span data-ttu-id="1b525-171">사용자 지정 개체에는 가져온 각각의 모듈 멤버를 나타내는 합성 멤버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-171">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="1b525-172">예를 들어 모듈의 함수와 cmdlet은 사용자 지정 개체의 스크립트 메서드로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-172">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="1b525-173">사용자 지정 개체는 스크립팅에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-173">Custom objects are useful in scripting.</span></span> <span data-ttu-id="1b525-174">또한 가져온 몇몇 개체의 이름이 같은 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-174">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="1b525-175">개체의 스크립트 메서드를 사용하는 것은 모듈 이름을 포함하여 가져온 멤버의 정규화된 이름을 지정하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-175">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="1b525-176">**AsCustomObject** 매개 변수는 스크립트 모듈을 가져오는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-176">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="1b525-177">사용 `Get-Module` 가능한 모듈 중 스크립트 모듈을 확인 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-177">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

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

<span data-ttu-id="1b525-178">`Show-Calendar` **AsCustomObject** 매개 변수를 사용 하 여 스크립트 모듈을 가져와서 사용자 지정 개체를 요청 하 고 **PassThru** 매개 변수를 사용 하 여 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-178">The `Show-Calendar` script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="1b525-179">결과 사용자 지정 개체는 변수에 저장 됩니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="1b525-179">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="1b525-180">`$a`변수는 `Get-Member` 저장 된 개체의 속성 및 메서드를 표시 하기 위해 cmdlet으로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-180">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="1b525-181">출력은 스크립트 메서드를 보여 줍니다 `Show-Calendar` .</span><span class="sxs-lookup"><span data-stu-id="1b525-181">The output shows a `Show-Calendar` script method.</span></span>

<span data-ttu-id="1b525-182">스크립트 메서드를 호출 하려면 `Show-Calendar` 이름에 하이픈이 포함 되므로 메서드 이름을 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-182">To call the `Show-Calendar` script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="1b525-183">예 8: 모듈을 동일한 세션으로 다시 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-183">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="1b525-184">이 예제에서는  `Import-Module` 모듈을 동일한 세션으로 다시 가져오는 때의 Force 매개 변수를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-184">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="1b525-185">**Force** 매개 변수는 로드 된 모듈을 제거한 다음 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-185">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="1b525-186">첫 번째 명령은 **Psdiagnostics** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-186">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="1b525-187">두 번째 명령은 모듈을 다시 가져오는데, 이번에는 **Prefix** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-187">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="1b525-188">**Force** 매개 변수를 사용 하지 않으면 세션에 각 **psdiagnostics** cmdlet의 복사본 두 개가 포함 됩니다. 하나에는 표준 이름과 접두사가 붙은 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-188">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="1b525-189">예제 9: 가져온 명령에 의해 숨겨진 명령 실행</span><span class="sxs-lookup"><span data-stu-id="1b525-189">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="1b525-190">이 예제에서는 가져온 명령에서 숨긴 명령을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-190">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="1b525-191">**Testmodule** 모듈에는 연도 `Get-Date` 와 날짜를 반환 하는 라는 함수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-191">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

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

<span data-ttu-id="1b525-192">첫 번째 `Get-Date` cmdlet은 현재 날짜를 사용 하 여 **DateTime** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-192">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="1b525-193">**Testmodule** 모듈을 가져온 후는 연도의 `Get-Date` 연도와 일자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-193">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="1b525-194">의 **all** 매개 변수를 사용 하 여 `Get-Command` `Get-Date` 세션의 모든 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-194">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="1b525-195">결과에는 세션에 두 개의 `Get-Date` 명령, 즉 **testmodule** 모듈의 함수 및 **Microsoft PowerShell** 모듈의 cmdlet이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-195">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="1b525-196">함수는 cmdlet 보다 우선 하므로 `Get-Date` cmdlet 대신 **testmodule** 모듈의 함수를 실행 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1b525-196">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="1b525-197">원래 버전의를 실행 하려면 `Get-Date` 모듈 이름으로 명령 이름을 정규화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-197">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="1b525-198">PowerShell의 명령 우선 순위에 대 한 자세한 내용은 [about_Command_Precedence](about/about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-198">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="1b525-199">예 10: 모듈의 최소 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-199">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="1b525-200">이 예제에서는 **PowerShellGet** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-200">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="1b525-201">의 **MinimumVersion** 매개 변수를 사용 하 여 `Import-Module` 버전 2.0.0 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-201">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="1b525-202">또한 **RequiredVersion** 매개 변수를 사용 하 여 모듈의 특정 버전을 가져오거나 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 `#Requires` 스크립트에서 모듈의 특정 버전을 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-202">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="1b525-203">예 11: 정규화 된 이름을 사용 하 여 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-203">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="1b525-204">이 예제에서는 FullyQualifiedName를 사용 하 여 모듈의 특정 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-204">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

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

### <span data-ttu-id="1b525-205">예 12: 정규화 된 경로를 사용 하 여 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-205">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="1b525-206">이 예에서는 정규화 된 경로를 사용 하 여 모듈의 특정 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-206">This example imports a specific version of a module using the fully qualified path.</span></span>

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

### <span data-ttu-id="1b525-207">예제 13: 원격 컴퓨터에서 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="1b525-207">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="1b525-208">이 예제에서는 cmdlet을 사용 하 여 `Import-Module` 원격 컴퓨터에서 모듈을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-208">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="1b525-209">이 명령은 PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-209">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="1b525-210">다른 세션에서 모듈을 가져오면 현재 세션에서 해당 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-210">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="1b525-211">그러나 cmdlet을 사용 하는 명령은 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-211">However, commands that use the cmdlets run in the remote session.</span></span>

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

<span data-ttu-id="1b525-212">`New-PSSession` Server01 컴퓨터에 대 한 원격 세션 (**PSSession**)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-212">`New-PSSession` creates a remote session (**PSSession**) to the Server01 computer.</span></span> <span data-ttu-id="1b525-213">**PSSession** 은 변수에 저장 됩니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="1b525-213">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="1b525-214">`Get-Module` **PSSession** 매개 변수를 사용 하 여를 실행 하는 경우 **netsecurity** 모듈이 설치 되어 원격 컴퓨터에 사용 가능 하다는 것을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-214">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="1b525-215">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Module` 원격 세션에서 명령을 실행 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-215">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="1b525-216">예: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="1b525-216">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="1b525-217">`Import-Module` **PSSession** 매개 변수를 사용 하 여를 실행 하면 원격 컴퓨터에서 현재 세션으로 **netsecurity** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-217">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="1b525-218">`Get-Command`Cmdlet은 **netsecurity** 모듈의 **get** 및 include **방화벽** 으로 시작 하는 명령을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-218">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="1b525-219">출력은 모듈과 해당 cmdlet을 현재 세션으로 가져왔는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-219">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="1b525-220">그런 다음 `Get-NetFirewallRule` cmdlet은 Server01 컴퓨터에 Windows 원격 관리 방화벽 규칙을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-220">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="1b525-221">이는 cmdlet을 사용 하 여 `Invoke-Command` `Get-NetFirewallRule` 원격 세션에서 실행 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-221">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="1b525-222">예 14: Windows 운영 체제를 사용 하지 않고 원격 컴퓨터의 저장소 관리</span><span class="sxs-lookup"><span data-stu-id="1b525-222">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="1b525-223">이 예에서는 컴퓨터의 관리자가 모듈 검색 WMI 공급자를 설치 하 여 공급자 용으로 설계 된 CIM 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-223">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="1b525-224">`New-CimSession`Cmdlet은 여 rsdgf03 이라는 원격 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-224">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="1b525-225">세션은 원격 컴퓨터의 WMI 서비스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-225">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="1b525-226">CIM 세션은 변수에 저장 됩니다 `$cs` .</span><span class="sxs-lookup"><span data-stu-id="1b525-226">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="1b525-227">`Import-Module` 는의 **CimSession** 를 사용 하 여 `$cs` 여 rsdgf03 컴퓨터에서 **저장소** CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-227">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="1b525-228">`Get-Command`Cmdlet은 `Get-Disk` **저장소** 모듈의 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-228">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="1b525-229">CIM 모듈을 로컬 세션으로 가져오면 PowerShell은 각 명령의 CDXML 파일을 로컬 세션의 함수로 표시 되는 PowerShell 스크립트로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-229">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="1b525-230">`Get-Disk`는 로컬 세션에서 형식화 되었지만 cmdlet은 해당 파일을 가져온 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-230">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="1b525-231">이 명령은 원격 컴퓨터에서 로컬 세션으로 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-231">The command returns objects from the remote computer to the local session.</span></span>

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

## <span data-ttu-id="1b525-232">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b525-232">PARAMETERS</span></span>

### <span data-ttu-id="1b525-233">-별칭</span><span class="sxs-lookup"><span data-stu-id="1b525-233">-Alias</span></span>

<span data-ttu-id="1b525-234">이 cmdlet이 모듈에서 현재 세션으로 가져오는 별칭을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-234">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="1b525-235">쉼표로 구분된 별칭 목록을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-235">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="1b525-236">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-236">Wildcard characters are permitted.</span></span>

<span data-ttu-id="1b525-237">모듈을 가져올 때 선택된 별칭을 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-237">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="1b525-238">이 매개 변수를 사용하면 내보내는 별칭 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-238">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="1b525-239">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="1b525-239">-ArgumentList</span></span>

<span data-ttu-id="1b525-240">명령 중에 스크립트 모듈로 전달 되는 인수 또는 매개 변수 값의 배열을 지정 합니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b525-240">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="1b525-241">이 매개 변수는 스크립트 모듈을 가져오는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-241">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="1b525-242">또한 **인수** 에 따라 **argumentlist** 매개 변수를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-242">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="1b525-243">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-243">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="1b525-244">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="1b525-244">-AsCustomObject</span></span>

<span data-ttu-id="1b525-245">이 cmdlet은 가져온 모듈 멤버를 나타내는 멤버가 있는 사용자 지정 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-245">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="1b525-246">이 매개 변수는 스크립트 모듈에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-246">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="1b525-247">**AsCustomObject** 매개 변수를 사용 하는 경우는 `Import-Module` 모듈 멤버를 세션으로 가져온 다음 **Psmoduleinfo** 개체 대신 **PSCustomObject** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-247">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="1b525-248">사용자 지정 개체를 변수에 저장하고 점 표기법을 사용하여 멤버를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-248">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

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

### <span data-ttu-id="1b525-249">-어셈블리</span><span class="sxs-lookup"><span data-stu-id="1b525-249">-Assembly</span></span>

<span data-ttu-id="1b525-250">어셈블리 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-250">Specifies an array of assembly objects.</span></span> <span data-ttu-id="1b525-251">이 cmdlet은 지정 된 어셈블리 개체에 구현 된 cmdlet 및 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-251">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="1b525-252">어셈블리 개체가 포함된 변수나 어셈블리 개체를 만드는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-252">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="1b525-253">어셈블리 개체를로 파이프 할 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b525-253">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="1b525-254">이 매개 변수를 사용하면 지정된 어셈블리에서 구현한 cmdlet과 공급자만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-254">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="1b525-255">모듈에 다른 파일이 포함 되어 있으면 해당 파일을 가져오지 않으며 모듈의 중요 한 멤버가 누락 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-255">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="1b525-256">모듈을 디버깅 하 고 테스트 하는 데이 매개 변수를 사용 하거나 모듈 작성자가 사용 하도록 지시 하는 경우이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-256">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

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

### <span data-ttu-id="1b525-257">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="1b525-257">-CimNamespace</span></span>

<span data-ttu-id="1b525-258">CIM 모듈을 표시하는 대체 CIM 공급자의 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-258">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="1b525-259">기본값은 모듈 검색 WMI 공급자의 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-259">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="1b525-260">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-260">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="1b525-261">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1b525-262">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="1b525-262">-CimResourceUri</span></span>

<span data-ttu-id="1b525-263">CIM 모듈의 대체 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-263">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="1b525-264">기본값은 원격 컴퓨터의 모듈 검색 WMI 공급자에 대 한 리소스 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-264">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="1b525-265">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-265">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="1b525-266">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1b525-267">-CimSession</span><span class="sxs-lookup"><span data-stu-id="1b525-267">-CimSession</span></span>

<span data-ttu-id="1b525-268">원격 컴퓨터에서 CIM 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-268">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="1b525-269">Cim 세션을 포함 하는 변수 또는 CIM 세션을 가져오는 명령 (예: [CimSession](../CimCmdlets/Get-CimSession.md) 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-269">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="1b525-270">`Import-Module` CIM 세션 연결을 사용 하 여 원격 컴퓨터에서 현재 세션으로 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-270">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="1b525-271">현재 세션에서 가져온 모듈의 명령을 사용 하면 명령이 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-271">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="1b525-272">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 Windows 컴퓨터에서 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-272">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="1b525-273">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-273">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1b525-274">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b525-274">-Cmdlet</span></span>

<span data-ttu-id="1b525-275">이 cmdlet이 모듈에서 현재 세션으로 가져오는 cmdlet의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-275">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="1b525-276">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="1b525-277">모듈을 가져올 때 선택된 cmdlet을 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-277">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="1b525-278">이 매개 변수를 사용하면 내보내는 cmdlet 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-278">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="1b525-279">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="1b525-279">-DisableNameChecking</span></span>

<span data-ttu-id="1b525-280">이 cmdlet은 이름에 승인 되지 않은 동사 나 금지 된 문자가 포함 된 cmdlet 또는 함수를 가져올 때 경고 메시지를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-280">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="1b525-281">기본적으로 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 PowerShell에서 다음과 같은 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-281">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="1b525-282">경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-282">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="1b525-283">자세한 내용을 보려면 Verbose 매개 변수를 사용하거나 승인된 동사 목록을 보려면 Get-Verb를 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-283">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="1b525-284">이 메시지는 경고일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-284">This message is only a warning.</span></span> <span data-ttu-id="1b525-285">비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-285">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="1b525-286">메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-286">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="1b525-287">-Force</span><span class="sxs-lookup"><span data-stu-id="1b525-287">-Force</span></span>

<span data-ttu-id="1b525-288">이 매개 변수를 통해 모듈을 로드 하거나 현재 모듈 위에 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-288">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

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

### <span data-ttu-id="1b525-289">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1b525-289">-FullyQualifiedName</span></span>

<span data-ttu-id="1b525-290">모듈의 정규화 된 이름을 해시 테이블로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-290">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="1b525-291">값은 문자열과 해시 테이블의 조합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-291">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="1b525-292">해시 테이블에는 다음과 같은 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-292">The hash table has the following keys.</span></span>

- <span data-ttu-id="1b525-293">`ModuleName` - **필수** 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-293">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="1b525-294">`GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-294">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="1b525-295">또한 아래 세 키 중 하나를 지정 **해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-295">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="1b525-296">이러한 키는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-296">These keys can't be used together.</span></span>
  - <span data-ttu-id="1b525-297">`ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-297">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="1b525-298">`RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-298">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="1b525-299">`MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-299">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedNameAndPSSession, FullyQualifiedName, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1b525-300">-함수</span><span class="sxs-lookup"><span data-stu-id="1b525-300">-Function</span></span>

<span data-ttu-id="1b525-301">이 cmdlet이 모듈에서 현재 세션으로 가져오는 함수 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-301">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="1b525-302">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-302">Wildcard characters are permitted.</span></span> <span data-ttu-id="1b525-303">모듈을 가져올 때 선택된 함수를 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-303">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="1b525-304">이 매개 변수를 사용하면 내보내는 함수 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-304">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="1b525-305">-전역</span><span class="sxs-lookup"><span data-stu-id="1b525-305">-Global</span></span>

<span data-ttu-id="1b525-306">이 cmdlet은 모듈을 전역 세션 상태로 가져오므로 세션의 모든 명령에서 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-306">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="1b525-307">기본적으로 `Import-Module` 명령 프롬프트, 스크립트 파일 또는 scriptblock에서 cmdlet을 호출 하면 모든 명령을 전역 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-307">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="1b525-308">다른 모듈에서 호출 되는 경우 `Import-Module` cmdlet은 중첩 모듈의 명령을 포함 하 여 모듈의 명령을 호출 하는 모듈의 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-308">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="1b525-309">`Import-Module`모듈 내에서를 호출 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-309">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="1b525-310">대신, 부모 모듈의 매니페스트에서 대상 모듈을 중첩 모듈로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-310">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="1b525-311">중첩 모듈을 선언 하면 종속성의 검색 기능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-311">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="1b525-312">**Global** 매개 변수는 **Global** 값을 사용하는 **Scope** 매개 변수와 동일한 결과를 낳습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-312">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="1b525-313">모듈에서 내보내는 명령을 제한 하려면 `Export-ModuleMember` 스크립트 모듈의 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-313">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

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

### <span data-ttu-id="1b525-314">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1b525-314">-MaximumVersion</span></span>

<span data-ttu-id="1b525-315">최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-315">Specifies a maximum version.</span></span> <span data-ttu-id="1b525-316">이 cmdlet은 지정 된 값 보다 작거나 같은 버전의 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-316">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="1b525-317">버전이 한정 되지 않은 경우는 `Import-Module` 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-317">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b525-318">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1b525-318">-MinimumVersion</span></span>

<span data-ttu-id="1b525-319">최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-319">Specifies a minimum version.</span></span> <span data-ttu-id="1b525-320">이 cmdlet은 지정 된 값 보다 크거나 같은 버전의 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-320">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="1b525-321">**MinimumVersion** 매개 변수 이름 또는 그 별칭인 **Version** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-321">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="1b525-322">버전이 한정 되지 않은 경우는 `Import-Module` 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-322">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="1b525-323">정확한 버전을 지정하려면 **RequiredVersion** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-323">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="1b525-324">**#Requires** 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 스크립트에서 모듈의 특정 버전을 요구할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-324">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="1b525-325">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b525-326">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="1b525-326">-ModuleInfo</span></span>

<span data-ttu-id="1b525-327">가져올 모듈 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-327">Specifies an array of module objects to import.</span></span> <span data-ttu-id="1b525-328">모듈 개체를 포함 하는 변수를 입력 하거나 모듈 개체를 가져오는 명령 (예:)을 입력 `Get-Module -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-328">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="1b525-329">모듈 개체를로 파이프 할 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b525-329">You can also pipe module objects to `Import-Module`.</span></span>

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

### <span data-ttu-id="1b525-330">-Name</span><span class="sxs-lookup"><span data-stu-id="1b525-330">-Name</span></span>

<span data-ttu-id="1b525-331">가져올 모듈의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-331">Specifies the names of the modules to import.</span></span> <span data-ttu-id="1b525-332">모듈 이름 또는 모듈의 파일 이름 (예: `.psd1` ,, `.psm1` `.dll` 또는 파일)을 입력 합니다 `.ps1` .</span><span class="sxs-lookup"><span data-stu-id="1b525-332">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="1b525-333">파일 경로는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-333">File paths are optional.</span></span> <span data-ttu-id="1b525-334">와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-334">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="1b525-335">모듈 이름 및 파일 이름을로 파이프 할 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b525-335">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="1b525-336">경로를 생략 하면는 `Import-Module` 환경 변수에 저장 된 경로에서 모듈을 찾습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="1b525-336">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="1b525-337">가능하면 항상 모듈 이름만 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-337">Specify only the module name whenever possible.</span></span> <span data-ttu-id="1b525-338">파일 이름을 지정하는 경우 해당 파일에 구현된 멤버만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-338">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="1b525-339">모듈에 다른 파일이 포함 되어 있으면 해당 파일을 가져오지 않으며 모듈의 중요 한 멤버가 누락 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-339">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="1b525-340">스크립트 파일 ()은 모듈로 가져올 수 있지만 스크립트 `.ps1` 파일은 일반적으로 스크립트 모듈 파일 () 파일 처럼 구조화 되지 않습니다 `.psm1` .</span><span class="sxs-lookup"><span data-stu-id="1b525-340">While it is possible to import a script (`.ps1`) file as a module, script files are usually not structured like script modules file (`.psm1`) file.</span></span> <span data-ttu-id="1b525-341">스크립트 파일을 가져오면 모듈로 사용할 수 있다는 보장이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-341">Importing a script file does not guarantee that it is usable as a module.</span></span> <span data-ttu-id="1b525-342">자세한 내용은 [about_Modules](about/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-342">For more information, see [about_Modules](about/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1b525-343">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="1b525-343">-NoClobber</span></span>

<span data-ttu-id="1b525-344">현재 세션에 있는 기존 명령과 이름이 동일한 명령을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-344">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="1b525-345">기본적으로는 `Import-Module` 내보낸 모든 모듈 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-345">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="1b525-346">이름이 같은 명령은 세션의 명령을 숨기 거 나 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-346">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="1b525-347">세션에서 명령 이름 충돌을 방지하려면 **Prefix** 또는 **NoClobber** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-347">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="1b525-348">이름 충돌 및 명령 우선 순위에 대한 자세한 내용은 [about_Modules](about/about_Modules.md) 및 [about_Command_Precedence](about/about_Command_Precedence.md)의 "모듈 및 이름 충돌"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-348">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="1b525-349">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-349">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1b525-350">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1b525-350">-PassThru</span></span>

<span data-ttu-id="1b525-351">작업 중인 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-351">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="1b525-352">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-352">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1b525-353">-접두사</span><span class="sxs-lookup"><span data-stu-id="1b525-353">-Prefix</span></span>

<span data-ttu-id="1b525-354">이 cmdlet이 가져온 모듈 멤버의 이름에 있는 명사에 추가 하는 접두사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-354">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="1b525-355">세션에 있는 서로 다른 멤버의 이름이 동일한 경우 발생할 수 있는 이름 충돌을 방지하려면 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-355">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="1b525-356">이 매개 변수는 모듈을 변경 하지 않으며 모듈에서 자체적으로 사용 하기 위해 가져오는 파일에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-356">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="1b525-357">이를 중첩 모듈 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-357">These are known as nested modules.</span></span> <span data-ttu-id="1b525-358">이 cmdlet은 현재 세션에 있는 멤버의 이름에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-358">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="1b525-359">예를 들어, 접두사 UTC를 지정 하 고 cmdlet을 가져오면이 `Get-Date` cmdlet은 세션에서로 알려져 `Get-UTCDate` 있으며 원래 cmdlet과는 혼동 되지 않습니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1b525-359">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="1b525-360">이 매개 변수 값은 기본 접두사를 지정하는 모듈의 **DefaultCommandPrefix** 속성보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-360">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="1b525-361">-PSSession</span><span class="sxs-lookup"><span data-stu-id="1b525-361">-PSSession</span></span>

<span data-ttu-id="1b525-362">이 cmdlet이 모듈을 현재 세션으로 가져오는 PowerShell 사용자 관리 세션 (**PSSession**)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-362">Specifies a PowerShell user-managed session (**PSSession**) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="1b525-363">**Pssession이** 포함 된 변수 또는 **pssession** 을 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1b525-363">Enter a variable that contains a **PSSession** or a command that gets a **PSSession**, such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="1b525-364">다른 세션에서 현재 세션으로 모듈을 가져오면 로컬 모듈의 cmdlet을 사용할 때와 마찬가지로 현재 세션에서 해당 모듈의 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-364">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="1b525-365">원격 cmdlet을 사용 하는 명령은 원격 세션에서 실행 되지만 원격 세부 정보는 PowerShell을 통해 백그라운드에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-365">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="1b525-366">이 매개 변수는 PowerShell의 암시적 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-366">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="1b525-367">Cmdlet을 사용 하 여 `Import-PSSession` 세션에서 특정 모듈을 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-367">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="1b525-368">`Import-Module` 다른 세션에서 PowerShell 핵심 모듈을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-368">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="1b525-369">PowerShell 핵심 모듈의 이름은 Microsoft. PowerShell로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-369">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="1b525-370">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-370">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1b525-371">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1b525-371">-RequiredVersion</span></span>

<span data-ttu-id="1b525-372">이 cmdlet이 가져오는 모듈의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-372">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="1b525-373">버전이 설치 되어 있지 않으면에서 `Import-Module` 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-373">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="1b525-374">기본적으로는 `Import-Module` 버전 번호를 확인 하지 않고 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-374">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="1b525-375">최소 버전을 지정하려면 **MinimumVersion** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-375">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="1b525-376">**#Requires** 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 스크립트에서 모듈의 특정 버전을 요구할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-376">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="1b525-377">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-377">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="1b525-378">**RequiredVersion** 을 사용 하 여 기존 버전의 windows 운영 체제에 포함 된 모듈을 가져오는 스크립트는 이후 버전의 windows 운영 체제에서 자동으로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-378">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="1b525-379">이는 Windows 운영 체제의 이후 릴리스에서 PowerShell 모듈 버전 번호가 기존 버전의 Windows 운영 체제에서 모듈 버전 번호 보다 높기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-379">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b525-380">-범위</span><span class="sxs-lookup"><span data-stu-id="1b525-380">-Scope</span></span>

<span data-ttu-id="1b525-381">이 cmdlet이 모듈을 가져올 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-381">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="1b525-382">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-382">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1b525-383">**전역**.</span><span class="sxs-lookup"><span data-stu-id="1b525-383">**Global**.</span></span> <span data-ttu-id="1b525-384">세션의 모든 명령에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-384">Available to all commands in the session.</span></span> <span data-ttu-id="1b525-385">**Global** 매개 변수를 사용하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-385">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="1b525-386">**로컬**.</span><span class="sxs-lookup"><span data-stu-id="1b525-386">**Local**.</span></span> <span data-ttu-id="1b525-387">현재 범위에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-387">Available only in the current scope.</span></span>

<span data-ttu-id="1b525-388">기본적으로 `Import-Module` 명령 프롬프트, 스크립트 파일 또는 scriptblock에서 cmdlet을 호출 하면 모든 명령을 전역 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-388">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="1b525-389">매개 변수를 사용 `-Scope Local` 하 여 모듈 콘텐츠를 스크립트 또는 scriptblock 범위로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-389">You can use the `-Scope Local` parameter to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="1b525-390">다른 모듈에서 호출 되는 경우 `Import-Module` cmdlet은 중첩 모듈의 명령을 포함 하 여 모듈의 명령을 호출자의 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-390">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="1b525-391">또는를 지정 하면 `-Scope Global` `-Global` 이 cmdlet이 모듈을 전역 세션 상태로 가져오므로 세션의 모든 명령에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-391">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="1b525-392">**Global** 매개 변수는 **Global** 값을 사용하는 **Scope** 매개 변수와 동일한 결과를 낳습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-392">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="1b525-393">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-393">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1b525-394">-Variable</span><span class="sxs-lookup"><span data-stu-id="1b525-394">-Variable</span></span>

<span data-ttu-id="1b525-395">이 cmdlet이 모듈에서 현재 세션으로 가져오는 변수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-395">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="1b525-396">변수의 목록을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-396">Enter a list of variables.</span></span> <span data-ttu-id="1b525-397">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-397">Wildcard characters are permitted.</span></span>

<span data-ttu-id="1b525-398">모듈을 가져올 때 선택된 변수를 해당 세션으로 자동으로 내보내는 모듈도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-398">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="1b525-399">이 매개 변수를 사용하면 내보내는 변수 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-399">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="1b525-400">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="1b525-400">-SkipEditionCheck</span></span>

<span data-ttu-id="1b525-401">필드에 대 한 검사를 건너뜁니다 `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="1b525-401">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="1b525-402">`"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"`해당 모듈이 `Core` 매니페스트 필드에서를 지정 하지 않는 경우 모듈 디렉터리에서 PowerShell Core로 모듈을 로드할 수 있습니다 `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="1b525-402">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="1b525-403">다른 경로에서 모듈을 가져올 때 검사가 수행 되지 않으므로이 스위치는 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-403">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="1b525-404">Linux 및 macOS에서이 스위치는 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-404">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="1b525-405">자세한 내용은 [about_PowerShell_Editions](About/about_PowerShell_Editions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-405">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="1b525-406">`Import-Module -SkipEditionCheck` 는 여전히 모듈을 가져오지 못할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-406">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="1b525-407">성공한 경우에도 모듈에서 명령을 호출 하면 나중에 호환 되지 않는 API를 사용 하려고 할 때 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-407">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedNameAndPSSession, FullyQualifiedName, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b525-408">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="1b525-408">-UseWindowsPowerShell</span></span>

<span data-ttu-id="1b525-409">Windows PowerShell 호환성 기능을 사용 하 여 모듈을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-409">Loads module using Windows PowerShell Compatibility functionality.</span></span> <span data-ttu-id="1b525-410">자세한 내용은 [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-410">See [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b525-411">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b525-411">CommonParameters</span></span>

<span data-ttu-id="1b525-412">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b525-412">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b525-413">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-413">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b525-414">입력</span><span class="sxs-lookup"><span data-stu-id="1b525-414">INPUTS</span></span>

### <span data-ttu-id="1b525-415">System.string, System.web.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="1b525-415">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="1b525-416">모듈 이름, 모듈 개체 또는 어셈블리 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-416">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="1b525-417">출력</span><span class="sxs-lookup"><span data-stu-id="1b525-417">OUTPUTS</span></span>

### <span data-ttu-id="1b525-418">None, PSCustomObject 또는. m i n. a p.</span><span class="sxs-lookup"><span data-stu-id="1b525-418">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="1b525-419">기본적으로는 `Import-Module` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-419">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="1b525-420">**PassThru** 매개 변수를 지정 하는 경우 cmdlet은 모듈을 나타내는 **system.object** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-420">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="1b525-421">**AsCustomObject** 매개 변수를 지정 하면 **PSCustomObject** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-421">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="1b525-422">참고</span><span class="sxs-lookup"><span data-stu-id="1b525-422">NOTES</span></span>

- <span data-ttu-id="1b525-423">모듈을 가져오려면 모듈이 로컬 컴퓨터에 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-423">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="1b525-424">즉, 모듈 디렉터리를 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-424">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="1b525-425">자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-425">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="1b525-426">**PSSession** 및 **CIMSession** 매개 변수를 사용하여 원격 컴퓨터에 설치된 모듈을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-426">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="1b525-427">그러나 이러한 모듈의 cmdlet을 사용 하는 명령은 원격 컴퓨터의 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-427">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="1b525-428">이름과 형식이 같은 멤버를 세션에 가져오는 경우 PowerShell은 기본적으로 마지막으로 가져온 멤버를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-428">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="1b525-429">변수와 별칭은 바뀌고 원본에는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-429">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="1b525-430">함수, cmdlet 및 공급자는 단순히 새 멤버로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-430">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="1b525-431">스냅인, 모듈 또는 함수 경로의 이름으로 명령 이름을 정규화 하 여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-431">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="1b525-432">모듈에서 가져온 명령에 대 한 형식 지정 데이터를 업데이트 하려면 cmdlet을 사용 `Update-FormatData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-432">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="1b525-433">`Update-FormatData` 는 모듈에서 가져온 세션의 명령에 대 한 형식 지정 데이터도 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-433">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="1b525-434">모듈에 대 한 형식 지정 파일이 변경 되 면 `Update-FormatData` 명령을 실행 하 여 가져온 명령에 대 한 형식 지정 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-434">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="1b525-435">모듈을 다시 가져올 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-435">You don't need to import the module again.</span></span>

- <span data-ttu-id="1b525-436">Windows PowerShell 3.0 부터는 PowerShell과 함께 설치 되는 핵심 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-436">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="1b525-437">Windows PowerShell 2.0 및 이후 버전의 PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 (**PSSnapins**)으로 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-437">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="1b525-438">예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-438">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="1b525-439">또한 cmdlet에서 시작한 것과 같은 원격 세션 `New-PSSession` 은 핵심 스냅인을 포함 하는 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-439">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="1b525-440">핵심 모듈과 함께 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-440">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="1b525-441">Windows PowerShell 2.0에서는 모듈을 가져올 때까지 **ExportedCmdlets** 및 **NestedModules** 속성 값과 같은 module 개체의 일부 속성 값이 채워지지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-441">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported.</span></span>

- <span data-ttu-id="1b525-442">Windows PowerShell 3.0 +와 호환 되지 않는 혼합 모드 어셈블리를 포함 하는 모듈을 가져오려고 시도 하면에서 `Import-Module` 다음과 같은 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-442">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0+, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="1b525-443">Import-Module: 혼합 모드 어셈블리는 런타임의 버전 ' v 2.0.50727 '에 대해 빌드 되었으며 추가 구성 정보 없이 4.0 런타임에 로드 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-443">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="1b525-444">이 오류는 Windows PowerShell 2.0 용으로 설계 된 모듈에 혼합 모듈 어셈블리가 하나 이상 포함 되어 있을 때 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-444">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly.</span></span> <span data-ttu-id="1b525-445">C + + 및 c #과 같은 관리 코드 및 관리 되지 않는 코드를 모두 포함 하는 혼합 모듈 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-445">A mixed-module assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="1b525-446">혼합 모드 어셈블리를 포함 하는 모듈을 가져오려면 다음 명령을 사용 하 여 Windows PowerShell 2.0을 시작한 후 명령을 다시 시도 하십시오 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b525-446">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="1b525-447">CIM 세션 기능을 사용하려면 원격 컴퓨터에 WS-Management 원격 기능과 CIM(Common Information Model) 표준에 대한 Microsoft 구현인 WMI(Windows Management Instrumentation)가 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-447">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="1b525-448">컴퓨터에도 모듈 검색 WMI 공급자 또는 동일한 기본 기능을 갖춘 대체 CIM 공급자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-448">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="1b525-449">Windows 운영 체제를 실행 하지 않는 컴퓨터 및 PowerShell이 있는 Windows 컴퓨터에서 CIM 세션 기능을 사용할 수 있지만 PowerShell 원격을 사용 하도록 설정 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-449">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="1b525-450">CIM 매개 변수를 사용 하 여 로컬 컴퓨터를 포함 하 여 PowerShell 원격을 사용 하도록 설정한 컴퓨터에서 CIM 모듈을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-450">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="1b525-451">로컬 컴퓨터에서 CIM 세션을 만드는 경우 PowerShell은 WMI 대신 DCOM을 사용 하 여 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-451">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="1b525-452">기본적으로는 `Import-Module` 하위 범위에서 호출 된 경우에도 전역 범위에서 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-452">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="1b525-453">최상위 범위 및 모든 하위 범위는 모듈의 내보낸 요소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-453">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="1b525-454">하위 항목 범위에서 `-Scope Local` 는 해당 범위 및 모든 하위 항목 범위로 가져오기를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-454">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="1b525-455">그러면 부모 범위에 가져온 멤버가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-455">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="1b525-456">`Get-Module` 현재 세션에 로드 된 모든 모듈을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-456">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="1b525-457">여기에는 하위 항목 범위에서 로컬로 로드 된 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-457">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="1b525-458">`Get-Command -Module modulename`현재 범위에서 로드 된 멤버를 확인 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-458">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="1b525-459">`Import-Module` 는 모듈에서 클래스 및 열거형 정의를 로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-459">`Import-Module` does not load class and enum definitions in the module.</span></span> <span data-ttu-id="1b525-460">`using module`스크립트의 시작 부분에 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-460">Use the `using module` statement at the beginning of your script.</span></span> <span data-ttu-id="1b525-461">클래스 및 열거형 정의를 포함 하 여 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1b525-461">This imports the module, including the class and enum definitions.</span></span> <span data-ttu-id="1b525-462">자세한 내용은 [about_Using](About/about_Using.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b525-462">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="1b525-463">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1b525-463">RELATED LINKS</span></span>

[<span data-ttu-id="1b525-464">about_Modules</span><span class="sxs-lookup"><span data-stu-id="1b525-464">about_Modules</span></span>](about/about_Modules.md)

[<span data-ttu-id="1b525-465">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="1b525-465">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="1b525-466">Get-Module</span><span class="sxs-lookup"><span data-stu-id="1b525-466">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="1b525-467">New-Module</span><span class="sxs-lookup"><span data-stu-id="1b525-467">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="1b525-468">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="1b525-468">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="1b525-469">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="1b525-469">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
