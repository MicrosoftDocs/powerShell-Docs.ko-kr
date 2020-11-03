---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: b3444b0670794b9cc65329cbaabc7e26dd131f64
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216122"
---
# <span data-ttu-id="0648a-103">Get-Module</span><span class="sxs-lookup"><span data-stu-id="0648a-103">Get-Module</span></span>

## <span data-ttu-id="0648a-104">개요</span><span class="sxs-lookup"><span data-stu-id="0648a-104">SYNOPSIS</span></span>
<span data-ttu-id="0648a-105">현재 세션으로 가져왔거나 가져올 수 있는 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-105">Gets the modules that have been imported or that can be imported into the current session.</span></span>

## <span data-ttu-id="0648a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0648a-106">SYNTAX</span></span>

### <span data-ttu-id="0648a-107">로드 됨 (기본값)</span><span class="sxs-lookup"><span data-stu-id="0648a-107">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="0648a-108">사용 가능</span><span class="sxs-lookup"><span data-stu-id="0648a-108">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="0648a-109">PsSession</span><span class="sxs-lookup"><span data-stu-id="0648a-109">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="0648a-110">CimSession</span><span class="sxs-lookup"><span data-stu-id="0648a-110">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="0648a-111">설명</span><span class="sxs-lookup"><span data-stu-id="0648a-111">DESCRIPTION</span></span>

<span data-ttu-id="0648a-112">`Get-Module`Cmdlet은 powershell 세션으로 가져오거나 가져올 수 있는 powershell 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-112">The `Get-Module` cmdlet gets the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span>
<span data-ttu-id="0648a-113">을 반환 하는 module 개체는 `Get-Module` 모듈에 대 한 중요 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-113">The module object that `Get-Module` returns contains valuable information about the module.</span></span>
<span data-ttu-id="0648a-114">모듈 개체를 및 cmdlet과 같은 다른 cmdlet으로 파이프 할 수도 있습니다 `Import-Module` `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="0648a-114">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="0648a-115">매개 변수가 없는 경우 `Get-Module` 현재 세션으로 가져온 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-115">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span>
<span data-ttu-id="0648a-116">설치 된 모듈을 모두 가져오려면 **ListAvailable** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-116">To get all installed modules, specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="0648a-117">`Get-Module` 모듈을 가져오지만 가져오지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-117">`Get-Module` gets modules, but it does not import them.</span></span>
<span data-ttu-id="0648a-118">Windows PowerShell 3.0부터 모듈의 명령을 사용할 때 모듈을 자동으로 가져오지만, `Get-Module` 자동 가져오기를 트리거하지 않는 명령이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-118">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span>
<span data-ttu-id="0648a-119">Cmdlet을 사용 하 여 모듈을 세션으로 가져올 수도 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0648a-119">You can also import the modules into your session by using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="0648a-120">Windows PowerShell 3.0 부터는 원격 세션에서 모듈을 가져온 다음 로컬 세션으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-120">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span>
<span data-ttu-id="0648a-121">이 전략은 PowerShell의 암시적 원격 기능을 사용 하며 cmdlet을 사용 하는 것과 같습니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="0648a-121">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="0648a-122">다른 세션에서 가져온 모듈에서 명령을 사용 하면 명령이 원격 세션에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-122">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="0648a-123">이 기능을 사용 하면 로컬 세션에서 원격 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-123">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="0648a-124">또한 Windows PowerShell 3.0부터 및를 사용 하 여 cmdlet `Get-Module` `Import-Module` 이 CDXML (CMDLET 정의 XML) 파일에 정의 되어 있는 CIM (CIM(Common Information Model)) 모듈을 가져오고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-124">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span>
<span data-ttu-id="0648a-125">이 기능을 사용 하면 c + +로 작성 된 코드 어셈블리와 같이 관리 되지 않는 코드 어셈블리에 구현 된 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="0648a-126">이러한 새로운 기능을 사용 하 여 `Get-Module` 및 `Import-Module` Cmdlet은 Windows 운영 체제를 실행 하는 컴퓨터와 다른 운영 체제를 실행 하는 컴퓨터를 포함 하는 이기종 기업을 관리 하기 위한 기본 도구가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-126">With these new features, the `Get-Module` and `Import-Module` cmdlets become primary tools for managing heterogeneous enterprises that include computers that run the Windows operating system and computers that run other operating systems.</span></span>

<span data-ttu-id="0648a-127">PowerShell 및 PowerShell 원격을 사용 하는 Windows 운영 체제를 실행 하는 원격 컴퓨터를 관리 하려면 원격 컴퓨터에 **pssession** 을 만든 다음의 **pssession** 매개 변수를 사용 `Get-Module` 하 여 **pssession** 에서 PowerShell 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-127">To manage remote computers that run the Windows operating system that have PowerShell and PowerShell remoting enabled, create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the **PSSession** .</span></span>
<span data-ttu-id="0648a-128">모듈을 가져온 다음 현재 세션에서 가져온 명령을 사용 하면 명령이 원격 컴퓨터의 **PSSession** 에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-128">When you import the modules, and then use the imported commands in the current session, the commands run implicitly in the **PSSession** on the remote computer.</span></span>
<span data-ttu-id="0648a-129">이 전략을 사용하여 원격 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-129">You can use this strategy to manage the remote computer.</span></span>

<span data-ttu-id="0648a-130">유사한 전략을 사용 하 여 PowerShell 원격을 사용 하지 않는 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-130">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="0648a-131">여기에는 Windows 운영 체제를 실행 하지 않는 컴퓨터와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 컴퓨터가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-131">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="0648a-132">원격 컴퓨터에서 CIM 세션을 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-132">Start by creating a CIM session on the remote computer.</span></span>
<span data-ttu-id="0648a-133">CIM 세션은 원격 컴퓨터의 WMI(Windows Management Instrumentation) (WMI)에 대 한 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-133">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>
<span data-ttu-id="0648a-134">그런 다음의 **CIMSession** 매개 변수를 사용 하 여 cim `Get-Module` 세션에서 cim 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-134">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span>
<span data-ttu-id="0648a-135">Cmdlet을 사용 하 여 CIM 모듈을 가져온 `Import-Module` 다음 가져온 명령을 실행 하면 명령이 원격 컴퓨터에서 암시적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-135">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span>
<span data-ttu-id="0648a-136">이 WMI 및 CIM 전략을 사용하여 원격 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-136">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="0648a-137">예제</span><span class="sxs-lookup"><span data-stu-id="0648a-137">EXAMPLES</span></span>

### <span data-ttu-id="0648a-138">예 1: 현재 세션으로 가져온 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-138">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="0648a-139">이 명령은 현재 세션으로 가져온 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-139">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="0648a-140">예 2: 설치 된 모듈 및 사용 가능한 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-140">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="0648a-141">이 명령은 컴퓨터에 설치되어 있고 현재 세션으로 가져올 수 있는 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-141">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="0648a-142">`Get-Module`**$env:P SModulePath** 환경 변수로 지정 된 경로에서 사용 가능한 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-142">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span>
<span data-ttu-id="0648a-143">**PSModulePath** 에 대한 자세한 내용은 [about_Modules](About/about_Modules.md) 및 [about_Environment_Variables](About/about_Environment_Variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0648a-143">For more information about **PSModulePath** , see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="0648a-144">예제 3: 내보낸 파일 모두 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-144">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="0648a-145">이 명령은 사용 가능한 모든 모듈의 내보낸 파일을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-145">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="0648a-146">예제 4: 정규화 된 이름으로 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-146">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
  Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="0648a-147">이 명령은 **FullyQualifiedName** 매개 변수를 사용 하 여 모듈의 정규화 된 이름을 지정 하 여 **Microsoft PowerShell 관리** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-147">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span>
<span data-ttu-id="0648a-148">그런 다음이 명령은 결과를 cmdlet으로 파이프 `Format-Table` 하 여 **이름** 및 **버전이** 열 머리글로 포함 된 테이블로 결과를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-148">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="0648a-149">예 5: 모듈의 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-149">Example 5: Get properties of a module</span></span>

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

<span data-ttu-id="0648a-150">이 명령은를 반환 하는 **Psmoduleinfo** 개체의 속성을 가져옵니다 `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="0648a-150">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span>
<span data-ttu-id="0648a-151">모듈 파일마다 하나의 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-151">There is one object for each module file.</span></span>

<span data-ttu-id="0648a-152">이러한 속성을 사용하여 모듈 개체의 형식을 지정하고 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-152">You can use the properties to format and filter the module objects.</span></span>
<span data-ttu-id="0648a-153">속성에 대 한 자세한 내용은 [Psmoduleinfo 속성](/dotnet/api/system.management.automation.psmoduleinfo)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0648a-153">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="0648a-154">출력에는 Windows PowerShell 3.0에 도입 된 새 속성 (예: Author 및 **CompanyName** ) **이** 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-154">The output includes the new properties, such as **Author** and **CompanyName** , that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="0648a-155">예제 6: 이름별로 모든 모듈 그룹화</span><span class="sxs-lookup"><span data-stu-id="0648a-155">Example 6: Group all modules by name</span></span>

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

<span data-ttu-id="0648a-156">이 명령은 가져온 모듈과 사용 가능한 모듈 파일을 모두 가져온 다음 모듈 이름별로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-156">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="0648a-157">이에 따라 각 스크립트에서 내보내는 모듈 파일을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-157">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="0648a-158">예제 7: 모듈 매니페스트 내용 표시</span><span class="sxs-lookup"><span data-stu-id="0648a-158">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="0648a-159">이러한 명령은 PowerShell **BitsTransfer** 모듈에 대 한 모듈 매니페스트의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-159">These commands display the contents of the module manifest for the PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="0648a-160">모듈에는 매니페스트 파일이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-160">Modules are not required to have manifest files.</span></span>
<span data-ttu-id="0648a-161">매니페스트 파일이 있는 경우 매니페스트 파일에는 버전 번호를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-161">When they do have a manifest file, the manifest file is required only to include a version number.</span></span>
<span data-ttu-id="0648a-162">그러나 매니페스트 파일에서 모듈, 해당 모듈의 요구 사항 및 내용에 대한 유용한 정보를 제공하는 경우도 많습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-162">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

<span data-ttu-id="0648a-163">첫 번째 명령은 BitsTransfer 모듈을 나타내는 PSModuleInfo 개체를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-163">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="0648a-164">개체를 `$m` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-164">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="0648a-165">두 번째 명령은 cmdlet을 사용 하 여 `Get-Content` 지정 된 경로에 있는 매니페스트 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-165">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="0648a-166">이 명령은 점 표기법을 사용하여 개체의 Path 속성에 저장되어 있는 매니페스트 파일의 경로를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-166">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="0648a-167">출력은 모듈 매니페스트의 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-167">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="0648a-168">예 8: 모듈 디렉터리에 파일 나열</span><span class="sxs-lookup"><span data-stu-id="0648a-168">Example 8: List files in module directory</span></span>

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

<span data-ttu-id="0648a-169">이 명령은 모듈의 디렉터리에 있는 파일을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-169">This command lists the files in the directory of the module.</span></span>
<span data-ttu-id="0648a-170">이는 모듈을 가져오기 전에 모듈에 있는 항목을 확인하는 또 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-170">This is another way to determine what is in a module before you import it.</span></span>
<span data-ttu-id="0648a-171">일부 모듈에는 모듈에 대해 설명하는 추가 정보 파일이나 도움말 파일이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-171">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="0648a-172">예 9: 컴퓨터에 설치 된 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-172">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="0648a-173">이러한 명령은 Server01 컴퓨터에 설치된 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-173">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="0648a-174">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-174">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="0648a-175">이 명령은 $s 변수에 **PSSession** 을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-175">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="0648a-176">두 번째 명령은의 **pssession** 및 **ListAvailable** 매개 변수를 사용 하 여 `Get-Module` $s 변수의 **pssession** 에 있는 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-176">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="0648a-177">다른 세션에서 cmdlet으로 모듈을 파이프 하는 경우는 `Import-Module` `Import-Module` 암시적 원격 기능을 사용 하 여 모듈을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-177">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span>
<span data-ttu-id="0648a-178">Cmdlet을 사용 하는 것과 같습니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="0648a-178">This is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="0648a-179">이 cmdlet은 현재 세션의 모듈에서 사용할 수 있지만 이러한 cmdlet을 사용하는 명령은 실제로 원격 세션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-179">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span>
<span data-ttu-id="0648a-180">자세한 내용은 [`Import-Module`](Import-Module.md) 및 [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0648a-180">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="0648a-181">예 10: Windows 운영 체제를 실행 하지 않는 컴퓨터 관리</span><span class="sxs-lookup"><span data-stu-id="0648a-181">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="0648a-182">이 예제의 명령을 사용 하면 Windows 운영 체제를 실행 하지 않는 원격 컴퓨터의 저장소 시스템을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-182">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="0648a-183">이 예제에서는 컴퓨터의 관리자가 모듈 검색 WMI 공급자를 설치했으므로 CIM 명령은 공급자용으로 설계된 기본값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-183">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

<span data-ttu-id="0648a-184">첫 번째 명령은 cmdlet을 사용 하 여 `New-CimSession` 여 rsdgf03 원격 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-184">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="0648a-185">이 세션은 원격 컴퓨터의 WMI에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-185">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="0648a-186">이 명령은 CIM 세션을 변수에 저장 합니다 `$cs` .</span><span class="sxs-lookup"><span data-stu-id="0648a-186">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="0648a-187">두 번째 명령은 변수의 CIM 세션을 사용 하 여 `$cs` `Get-Module` 여 rsdgf03 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-187">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="0648a-188">이 명령은 Name 매개 변수를 사용하여 스토리지 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-188">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="0648a-189">이 명령은 파이프라인 연산자 (|)를 사용 하 여 저장소 모듈을 cmdlet으로 보내고 `Import-Module` ,이 cmdlet은 로컬 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-189">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="0648a-190">세 번째 명령은 `Get-Command` `Get-Disk` 저장소 모듈의 명령에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-190">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="0648a-191">CIM 모듈을 로컬 세션으로 가져오면 PowerShell에서 CIM 모듈을 나타내는 CDXML 파일을 로컬 세션의 함수로 표시 되는 PowerShell 스크립트로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-191">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="0648a-192">네 번째 명령은 명령을 실행 합니다 `Get-Disk` .</span><span class="sxs-lookup"><span data-stu-id="0648a-192">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="0648a-193">로컬 세션에서 이 명령을 입력하면 이 명령은 가져온 원격 컴퓨터에서 암시적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-193">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="0648a-194">이 명령은 원격 컴퓨터에서 개체를 검색하여 로컬 세션에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-194">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="0648a-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0648a-195">PARAMETERS</span></span>

### <span data-ttu-id="0648a-196">-All</span><span class="sxs-lookup"><span data-stu-id="0648a-196">-All</span></span>

<span data-ttu-id="0648a-197">이 cmdlet은 중첩 된 모듈, 매니페스트 (. psd1) 파일, 스크립트 모듈 (.psm1) 파일 및 이진 모듈 (.dll) 파일을 포함 하 여 각 모듈 폴더의 모든 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-197">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span>
<span data-ttu-id="0648a-198">이 매개 변수를 사용 하지 않으면 `Get-Module` 각 모듈 폴더의 기본 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-198">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-199">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="0648a-199">-CimNamespace</span></span>

<span data-ttu-id="0648a-200">CIM 모듈을 표시하는 대체 CIM 공급자의 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-200">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span>
<span data-ttu-id="0648a-201">기본값은 모듈 검색 WMI 공급자의 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-201">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="0648a-202">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-202">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="0648a-203">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="0648a-204">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="0648a-204">-CimResourceUri</span></span>

<span data-ttu-id="0648a-205">CIM 모듈의 대체 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-205">Specifies an alternate location for CIM modules.</span></span>
<span data-ttu-id="0648a-206">기본값은 원격 컴퓨터의 모듈 검색 WMI 공급자에 대 한 리소스 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-206">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="0648a-207">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-207">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="0648a-208">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="0648a-209">-CimSession</span><span class="sxs-lookup"><span data-stu-id="0648a-209">-CimSession</span></span>

<span data-ttu-id="0648a-210">원격 컴퓨터에서 CIM 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-210">Specifies a CIM session on the remote computer.</span></span>
<span data-ttu-id="0648a-211">Cim 세션을 포함 하는 변수 또는 CIM 세션을 가져오는 명령 (예: [CimSession](/powershell/module/cimcmdlets/get-cimsession) 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-211">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="0648a-212">`Get-Module` CIM 세션 연결을 사용 하 여 원격 컴퓨터에서 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-212">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span>
<span data-ttu-id="0648a-213">Cmdlet을 사용 하 여 모듈을 가져오고 `Import-Module` 현재 세션에서 가져온 모듈의 명령을 사용 하면 명령이 실제로 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-213">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="0648a-214">이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 컴퓨터에서 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-214">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="0648a-215">**CimSession** 매개 변수는 **CIMSession** 에서 모든 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-215">The **CimSession** parameter gets all modules in the **CIMSession** .</span></span>
<span data-ttu-id="0648a-216">그러나 CIM 기반 및 CDXML(Cmdlet 정의 XML) 기반 모듈만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-216">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="0648a-217">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0648a-217">-FullyQualifiedName</span></span>

<span data-ttu-id="0648a-218">**ModuleSpecification** 개체 형식으로 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-218">Specifies names of modules in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="0648a-219">이러한 개체는 MSDN library의 [ModuleSpecification 생성자 (Hashtable)](https://msdn.microsoft.com/library/jj136290) 의 설명 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-219">These objects are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="0648a-220">예를 들어 **FullyQualifiedName** 매개 변수는 다음 형식으로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-220">For example, the **FullyQualifiedName** parameter accepts a module name that is specified in the following formats:</span></span>

- <span data-ttu-id="0648a-221">@ {ModuleName = "ModuleName"; ModuleVersion = "version_number"}</span><span class="sxs-lookup"><span data-stu-id="0648a-221">@{ModuleName = "modulename"; ModuleVersion = "version_number"}</span></span>
- <span data-ttu-id="0648a-222">@ {ModuleName = "ModuleName"; ModuleVersion = "version_number"; Guid = "GUID"}</span><span class="sxs-lookup"><span data-stu-id="0648a-222">@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}</span></span>

<span data-ttu-id="0648a-223">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-223">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="0648a-224">**Name** 매개 변수와 동일한 명령에 **FullyQualifiedName** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-224">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-225">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="0648a-225">-ListAvailable</span></span>

<span data-ttu-id="0648a-226">이 cmdlet은 설치 된 모든 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-226">Indicates that this cmdlet gets all installed modules.</span></span>
<span data-ttu-id="0648a-227">`Get-Module`**PSModulePath** 환경 변수에 나열 된 경로에서 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-227">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="0648a-228">이 매개 변수를 사용 하지 않으면 `Get-Module` **PSModulePath** 환경 변수에 나열 되어 있고 현재 세션에 로드 된 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-228">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span>
<span data-ttu-id="0648a-229">**ListAvailable** 은 해당 모듈이 현재 세션에 로드된 경우에도 **PSModulePath** 환경 변수에 없는 모듈에 대한 정보를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-229">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-230">-Name</span><span class="sxs-lookup"><span data-stu-id="0648a-230">-Name</span></span>

<span data-ttu-id="0648a-231">이 cmdlet이 가져오는 모듈의 이름 또는 이름 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-231">Specifies names or name patterns of modules that this cmdlet gets.</span></span>
<span data-ttu-id="0648a-232">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-232">Wildcard characters are permitted.</span></span>
<span data-ttu-id="0648a-233">이름을로 파이프 할 수도 있습니다 `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="0648a-233">You can also pipe the names to `Get-Module`.</span></span>
<span data-ttu-id="0648a-234">**Name** 매개 변수와 동일한 명령에 **FullyQualifiedName** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-234">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="0648a-235">**이름** 에서 모듈 GUID를 값으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-235">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="0648a-236">GUID를 지정 하 여 모듈을 반환 하려면 대신 **FullyQualifiedName** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-236">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0648a-237">-PSSession</span><span class="sxs-lookup"><span data-stu-id="0648a-237">-PSSession</span></span>

<span data-ttu-id="0648a-238">지정 된 사용자 관리 PowerShell 세션 ( **PSSession** )에서 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-238">Gets the modules in the specified user-managed PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="0648a-239">세션을 포함 하는 변수, 세션을 가져오는 명령 (예: 명령) `Get-PSSession` 또는 세션을 만드는 명령 (예: 명령)을 입력 합니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="0648a-239">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="0648a-240">세션이 원격 컴퓨터에 연결 된 경우 **ListAvailable** 매개 변수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-240">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="0648a-241">`Get-Module` **Pssession** 매개 변수를 사용 하는 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Module -ListAvailable` **pssession** 에서 명령을 실행 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-241">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession** .</span></span>

<span data-ttu-id="0648a-242">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-242">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-243">-새로 고침</span><span class="sxs-lookup"><span data-stu-id="0648a-243">-Refresh</span></span>

<span data-ttu-id="0648a-244">이 cmdlet은 설치 된 명령의 캐시를 새로 고치도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-244">Indicates that this cmdlet refreshes the cache of installed commands.</span></span>
<span data-ttu-id="0648a-245">명령 캐시는 세션이 시작될 때 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-245">The command cache is created when the session starts.</span></span>
<span data-ttu-id="0648a-246">Cmdlet을 사용 하 여 `Get-Command` 세션으로 가져오지 않은 모듈에서 명령을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-246">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="0648a-247">이 매개 변수는 세션이 시작된 이후 모듈의 내용이 변경된 개발 및 테스트 시나리오에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-247">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="0648a-248">명령에서 **Refresh** 매개 변수를 지정 하는 경우 **ListAvailable** 을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-248">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable** .</span></span>

<span data-ttu-id="0648a-249">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-250">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="0648a-250">-PSEdition</span></span>

<span data-ttu-id="0648a-251">지정 된 버전의 PowerShell을 지 원하는 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-251">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="0648a-252">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0648a-253">데스크톱</span><span class="sxs-lookup"><span data-stu-id="0648a-253">Desktop</span></span>
- <span data-ttu-id="0648a-254">핵심</span><span class="sxs-lookup"><span data-stu-id="0648a-254">Core</span></span>

<span data-ttu-id="0648a-255">Get-Module cmdlet은 지정 된 값에 대 한 **Psmoduleinfo** 개체의 **CompatiblePSEditions** 속성을 확인 하 고 해당 속성이 설정 된 모듈만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-255">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="0648a-256">**데스크톱 버전:** .NET Framework 기반으로 하는 windows PowerShell 5.1 및 대부분의 Windows 버전에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-256">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell 5.1 and below on most Windows editions.</span></span>
> - <span data-ttu-id="0648a-257">**핵심 버전:** .NET Core를 기반으로 구축 된 PowerShell Core 6.0 이상 및 Windows IoT 및 Windows Nanoserver 용으로 빌드된 일부 Windows PowerShell 5.1 버전에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-257">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above, as well as some editions of Windows PowerShell 5.1 built for Windows IoT and Windows Nanoserver.</span></span> <span data-ttu-id="0648a-258">> 변수를 사용 하 여 현재 PowerShell 세션의 버전을 찾을 수 있습니다 `$PSEdition` .</span><span class="sxs-lookup"><span data-stu-id="0648a-258">> The edition of the current PowerShell session can be found with the `$PSEdition` variable.</span></span>

```yaml
Type: System.String
Parameter Sets: Available, PsSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-259">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="0648a-259">-SkipEditionCheck</span></span>

<span data-ttu-id="0648a-260">필드의 검사를 건너뜁니다 `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="0648a-260">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="0648a-261">기본적으로 Get-Module는 디렉터리에서 필드에를 지정 하지 않은 모듈을 생략 `%windir%\System32\WindowsPowerShell\v1.0\Modules` `Core` `CompatiblePSEditions` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-261">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span>
<span data-ttu-id="0648a-262">이 스위치가 설정 되 면가 없는 모듈이 `Core` 포함 되므로 Powershell Core와 호환 되지 않는 Windows powershell 모듈 경로 아래의 모듈이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-262">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="0648a-263">MacOS 및 Linux에서이 매개 변수는 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-263">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="0648a-264">자세한 내용은 [about_PowerShell_Editions](About/about_PowerShell_Editions.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0648a-264">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0648a-265">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0648a-265">CommonParameters</span></span>

<span data-ttu-id="0648a-266">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0648a-266">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0648a-267">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0648a-267">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0648a-268">입력</span><span class="sxs-lookup"><span data-stu-id="0648a-268">INPUTS</span></span>

### <span data-ttu-id="0648a-269">System.String</span><span class="sxs-lookup"><span data-stu-id="0648a-269">System.String</span></span>

<span data-ttu-id="0648a-270">모듈 이름을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-270">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="0648a-271">출력</span><span class="sxs-lookup"><span data-stu-id="0648a-271">OUTPUTS</span></span>

### <span data-ttu-id="0648a-272">System.object..</span><span class="sxs-lookup"><span data-stu-id="0648a-272">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="0648a-273">이 cmdlet은 모듈을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-273">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="0648a-274">**ListAvailable** 매개 변수를 지정 하면는 `Get-Module` 동일한 속성 및 메서드를 포함 하는 **psmoduleinfo** 개체의 유형인 **moduleinfogrouping** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-274">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="0648a-275">참고</span><span class="sxs-lookup"><span data-stu-id="0648a-275">NOTES</span></span>

- <span data-ttu-id="0648a-276">Windows PowerShell 3.0부터 PowerShell에 포함 된 핵심 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-276">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="0648a-277">**Add-pssnapin** (스냅인) 인 **Microsoft. PowerShell** 은 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-277">The exception is **Microsoft.PowerShell.Core** , which is a snap-in ( **PSSnapin** ).</span></span> <span data-ttu-id="0648a-278">기본적으로 **Microsoft.PowerShell.Core** 스냅인만 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-278">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="0648a-279">모듈은 처음 사용할 때 자동으로 가져오며 cmdlet을 사용 하 여 가져올 수 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0648a-279">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>
- <span data-ttu-id="0648a-280">Windows PowerShell 3.0 부터는 PowerShell과 함께 설치 되는 핵심 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-280">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="0648a-281">Windows PowerShell 2.0 및 이후 버전의 PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 ( **PSSnapins** )으로 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-281">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="0648a-282">예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-282">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="0648a-283">또한 cmdlet에서 시작한 것과 같은 원격 세션 `New-PSSession` 은 핵심 스냅인을 포함 하는 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-283">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="0648a-284">핵심 모듈을 사용 하 여 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 MSDN Library의 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0648a-284">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

- <span data-ttu-id="0648a-285">`Get-Module`**PSModulePath** 환경 변수 ($Env:P SModulePath)의 값에 저장 된 위치의 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-285">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="0648a-286">Cmdlet의 **Path** 매개 변수를 사용 하 여 `Import-Module` 다른 위치의 모듈을 가져올 수 있지만 cmdlet을 사용 하 여 가져올 수는 없습니다 `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="0648a-286">You can use the **Path** parameter of the `Import-Module` cmdlet to import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>
- <span data-ttu-id="0648a-287">또한 PowerShell 3.0 부터는를 `Get-Module` 가져오기 전에 모듈을 더 쉽게 학습할 수 있도록를 반환 하는 개체에 새 속성이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-287">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="0648a-288">가져오기 전에 모든 속성이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-288">All properties are populated before importing.</span></span> <span data-ttu-id="0648a-289">여기에는 모듈에서 내보내는 명령을 나열 하는 **ExportedCommands** , **ExportedCmdlets** 및 **ExportedFunctions** 속성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-289">These include the **ExportedCommands** , **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>
- <span data-ttu-id="0648a-290">**ListAvailable** 매개 변수는 올바른 형식의 모듈만 가져옵니다. 즉, 기본 이름이 모듈 폴더의 이름과 동일한 파일이 하나 이상 포함 된 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-290">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="0648a-291">기본 이름은 파일 이름 확장명이 없는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-291">The base name is the name without the file name extension.</span></span> <span data-ttu-id="0648a-292">이름이 다른 파일을 포함 하는 폴더는 모듈이 아니라 컨테이너로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-292">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="0648a-293">.Dll 파일로 구현 되었지만 모듈 폴더에 포함 되지 않은 모듈을 가져오려면 **ListAvailable** 및 **All** 매개 변수를 모두 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-293">To get modules that are implemented as .dll files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="0648a-294">CIM 세션 기능을 사용하려면 원격 컴퓨터에 WS-Management 원격 기능과 CIM(Common Information Model) 표준에 대한 Microsoft 구현인 WMI(Windows Management Instrumentation)가 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-294">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="0648a-295">또한 컴퓨터에 모듈 검색 WMI 공급자나 동일한 기본 기능을 갖춘 대체 WMI 공급자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-295">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="0648a-296">Windows 운영 체제를 실행 하지 않는 컴퓨터 및 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 Windows 컴퓨터에서 CIM 세션 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-296">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="0648a-297">또한 CIM 매개 변수를 사용 하 여 PowerShell 원격을 사용 하도록 설정한 컴퓨터에서 CIM 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-297">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="0648a-298">여기에는 로컬 컴퓨터가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-298">This includes the local computer.</span></span>
<span data-ttu-id="0648a-299">로컬 컴퓨터에서 CIM 세션을 만드는 경우 PowerShell은 WMI 대신 DCOM을 사용 하 여 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0648a-299">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="0648a-300">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0648a-300">RELATED LINKS</span></span>

[<span data-ttu-id="0648a-301">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="0648a-301">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="0648a-302">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="0648a-302">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="0648a-303">about_Modules</span><span class="sxs-lookup"><span data-stu-id="0648a-303">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="0648a-304">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="0648a-304">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="0648a-305">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="0648a-305">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="0648a-306">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="0648a-306">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="0648a-307">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0648a-307">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="0648a-308">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="0648a-308">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="0648a-309">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="0648a-309">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
