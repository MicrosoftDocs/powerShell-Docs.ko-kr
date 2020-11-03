---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 8177b1ed45f6d6cdabf13670e36be4fcbb55a77b
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239954"
---
# <span data-ttu-id="11a0d-103">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="11a0d-103">New-ModuleManifest</span></span>

## <span data-ttu-id="11a0d-104">개요</span><span class="sxs-lookup"><span data-stu-id="11a0d-104">SYNOPSIS</span></span>
<span data-ttu-id="11a0d-105">새 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-105">Creates a new module manifest.</span></span>

## <span data-ttu-id="11a0d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="11a0d-106">SYNTAX</span></span>

### <span data-ttu-id="11a0d-107">모두</span><span class="sxs-lookup"><span data-stu-id="11a0d-107">All</span></span>

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="11a0d-108">설명</span><span class="sxs-lookup"><span data-stu-id="11a0d-108">DESCRIPTION</span></span>

<span data-ttu-id="11a0d-109">`New-ModuleManifest`Cmdlet은 새 모듈 매니페스트 ( `.psd1` ) 파일을 만들고 해당 값을 채운 다음 지정 된 경로에 매니페스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-109">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="11a0d-110">모듈 작성자는 이 cmdlet을 사용하여 모듈의 매니페스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-110">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="11a0d-111">모듈 매니페스트는 `.psd1` 해시 테이블을 포함 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-111">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="11a0d-112">해시 테이블의 키와 값은 모듈의 내용 및 특성을 설명하고, 필수 구성 요소를 정의하고, 구성 요소의 처리 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-112">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="11a0d-113">모듈에는 매니페스트가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-113">Manifests aren't required for a module.</span></span>

<span data-ttu-id="11a0d-114">`New-ModuleManifest` 일반적으로 사용 되는 모든 매니페스트 키를 포함 하는 매니페스트를 만들어 기본 출력을 매니페스트 템플릿으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-114">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="11a0d-115">값을 추가 또는 변경 하거나이 cmdlet이 추가 하지 않는 모듈 키를 추가 하려면 결과 파일을 텍스트 편집기에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-115">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="11a0d-116">**Path** 및 **PassThru** 를 제외 하 고 각 매개 변수는 모듈 매니페스트 키와 해당 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-116">Each parameter, except for **Path** and **PassThru** , creates a module manifest key and its value.</span></span>
<span data-ttu-id="11a0d-117">모듈 매니페스트에서는 **ModuleVersion** 키만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-117">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="11a0d-118">매개 변수 설명에 지정 된 경우를 제외 하 고, 명령에서 매개 변수를 생략 하면는 영향을 주지 `New-ModuleManifest` 않는 관련 값에 대 한 주석 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-118">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="11a0d-119">PowerShell 2.0에서는 `New-ModuleManifest` 필수 매개 변수 값 외에 명령에 지정 되지 않은 일반적으로 사용 되는 매개 변수의 값을 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-119">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="11a0d-120">PowerShell 3.0부터는 `New-ModuleManifest` 필요한 매개 변수 값이 지정 되지 않은 경우에만 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-120">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="11a0d-121">PowerShell 갤러리에 모듈을 게시 하려는 경우 매니페스트에 특정 속성에 대 한 값이 포함 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-121">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="11a0d-122">자세한 내용은 갤러리 설명서의 [PowerShell 갤러리에 게시 된 항목에 대 한 필수 메타 데이터](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-122">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="11a0d-123">예제</span><span class="sxs-lookup"><span data-stu-id="11a0d-123">EXAMPLES</span></span>

### <span data-ttu-id="11a0d-124">예제 1-새 모듈 매니페스트 만들기</span><span class="sxs-lookup"><span data-stu-id="11a0d-124">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="11a0d-125">이 예제에서는 **Path** 매개 변수로 지정 된 파일에 새 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-125">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="11a0d-126">**PassThru** 매개 변수는 출력을 파이프라인과 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-126">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="11a0d-127">출력은 매니페스트에 있는 모든 키의 기본값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-127">The output shows the default values of all keys in the manifest.</span></span>

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        # RequireLicenseAcceptance = $false

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

### <span data-ttu-id="11a0d-128">예제 2-미리 채워진 설정을 사용 하 여 새 매니페스트 만들기</span><span class="sxs-lookup"><span data-stu-id="11a0d-128">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="11a0d-129">이 예제에서는 새 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-129">This example creates a new module manifest.</span></span> <span data-ttu-id="11a0d-130">**PowerShellVersion** 및 **AliasesToExport** 매개 변수를 사용하여 해당 매니페스트 키에 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-130">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="11a0d-131">예제 3-다른 모듈이 필요한 매니페스트 만들기</span><span class="sxs-lookup"><span data-stu-id="11a0d-131">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="11a0d-132">이 예에서는 문자열 형식을 사용 하 여 **BitsTransfer** 모듈의 이름을 지정 하 고 해시 테이블 형식을 사용 하 여 이름, **GUID** 및 **PSScheduledJob** 모듈의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-132">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID** , and a version of the **PSScheduledJob** module.</span></span>

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="11a0d-133">이 예에서는 **Modulelist** , **RequiredModules** 및 **NestedModules** 매개 변수의 문자열 및 해시 테이블 형식을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-133">This example shows how to use the string and hash table formats of the **ModuleList** , **RequiredModules** , and **NestedModules** parameter.</span></span> <span data-ttu-id="11a0d-134">동일한 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-134">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="11a0d-135">예제 4-업데이트할 수 있는 도움말을 지 원하는 매니페스트 만들기</span><span class="sxs-lookup"><span data-stu-id="11a0d-135">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="11a0d-136">이 예제에서는 **HelpInfoUri** 매개 변수를 사용 하 여 모듈 매니페스트에 **HelpInfoUri** 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-136">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="11a0d-137">매개 변수 및 키의 값은 **http** 또는 **https** 로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-137">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="11a0d-138">이 값은 업데이트할 수 있는 도움말 시스템에 모듈에 대한 HelpInfo XML 업데이트할 수 있는 도움말 정보 파일이 있는 위치를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-138">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="11a0d-139">업데이트할 수 있는 도움말에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-139">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="11a0d-140">HelpInfo XML 파일에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-140">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="11a0d-141">예 5-모듈 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11a0d-141">Example 5 - Getting module information</span></span>

<span data-ttu-id="11a0d-142">이 예제에서는 모듈의 구성 값을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-142">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="11a0d-143">모듈 매니페스트의 값은 module 개체의 속성 값에 반영 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-143">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="11a0d-144">`Get-Module`Cmdlet은 **List** 매개 변수를 사용 하 여 **Microsoft. PowerShell 진단** 모듈을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-144">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="11a0d-145">이 명령은 모듈을 cmdlet에 전송 `Format-List` 하 여 모듈 개체의 모든 속성과 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-145">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## <span data-ttu-id="11a0d-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="11a0d-146">PARAMETERS</span></span>

### <span data-ttu-id="11a0d-147">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="11a0d-147">-AliasesToExport</span></span>

<span data-ttu-id="11a0d-148">모듈이 내보내는 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-148">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="11a0d-149">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-149">Wildcards are permitted.</span></span>

<span data-ttu-id="11a0d-150">이 매개 변수를 사용하여 모듈이 내보내는 별칭을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-150">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="11a0d-151">내보낸 별칭 목록에서 별칭을 제거할 수 있지만 목록에 별칭을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-151">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="11a0d-152">이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **AliasesToExport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 별칭을 매니페스트에서 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-152">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="11a0d-153">-작성자</span><span class="sxs-lookup"><span data-stu-id="11a0d-153">-Author</span></span>

<span data-ttu-id="11a0d-154">모듈 작성자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-154">Specifies the module author.</span></span>

<span data-ttu-id="11a0d-155">이 매개 변수를 생략 하면에서 `New-ModuleManifest` 현재 사용자의 이름으로 **Author** 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-155">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-156">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="11a0d-156">-ClrVersion</span></span>

<span data-ttu-id="11a0d-157">모듈에 필요한 Microsoft .NET Framework의 CLR(공용 언어 런타임) 최소 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-157">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-158">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="11a0d-158">-CmdletsToExport</span></span>

<span data-ttu-id="11a0d-159">모듈이 내보내는 cmdlet을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-159">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="11a0d-160">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-160">Wildcards are permitted.</span></span>

<span data-ttu-id="11a0d-161">이 매개 변수를 사용하여 모듈이 내보내는 cmdlet을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-161">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="11a0d-162">이 cmdlet은 내보낸 cmdlet 목록에서 cmdlet을 제거할 수 있지만 목록에 cmdlet을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-162">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="11a0d-163">이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **Cmdletstoexport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 cmdlet을 매니페스트에서 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-163">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="11a0d-164">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="11a0d-164">-CompanyName</span></span>

<span data-ttu-id="11a0d-165">모듈을 만든 회사나 공급업체를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-165">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="11a0d-166">이 매개 변수를 생략 하면는 `New-ModuleManifest` "Unknown" 값을 사용 하 여 **CompanyName** 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-166">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-167">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="11a0d-167">-CompatiblePSEditions</span></span>

<span data-ttu-id="11a0d-168">모듈의 호환 되는 Pseditions가를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-168">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="11a0d-169">PSEdition에 대 한 자세한 내용은 [호환 되는 PowerShell 버전이 있는 모듈](/powershell/scripting/gallery/concepts/module-psedition-support)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-169">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-170">-저작권</span><span class="sxs-lookup"><span data-stu-id="11a0d-170">-Copyright</span></span>

<span data-ttu-id="11a0d-171">모듈의 저작권 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-171">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="11a0d-172">이 매개 변수를 생략 하면 `New-ModuleManifest` 는 값을 갖는 **저작권** 키를 만듭니다 `(c) <year> <username>. All rights reserved.` `<year>` . 여기서는 현재 연도이 고 `<username>` 은 **Author** 키의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-172">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-173">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="11a0d-173">-DefaultCommandPrefix</span></span>

<span data-ttu-id="11a0d-174">세션으로 가져올 때 모듈에 있는 모든 명령의 명사 앞에 추가할 접두사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-174">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="11a0d-175">접두사 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-175">Enter a prefix string.</span></span> <span data-ttu-id="11a0d-176">접두사는 사용자 세션에서 명령 이름 충돌을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-176">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="11a0d-177">모듈 사용자는 cmdlet의 **prefix** 매개 변수를 지정 하 여이 접두사를 재정의할 수 있습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-177">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="11a0d-178">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-178">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="11a0d-179">-Description</span><span class="sxs-lookup"><span data-stu-id="11a0d-179">-Description</span></span>

<span data-ttu-id="11a0d-180">모듈의 내용을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-180">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="11a0d-181">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="11a0d-181">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="11a0d-182">모듈에 필요한 Microsoft .NET Framework의 최소 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-182">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-183">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="11a0d-183">-DscResourcesToExport</span></span>

<span data-ttu-id="11a0d-184">모듈에서 내보내는 DSC (Desired State Configuration) 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-184">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="11a0d-185">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-185">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="11a0d-186">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="11a0d-186">-ExternalModuleDependencies</span></span>

<span data-ttu-id="11a0d-187">이 모듈이 종속 된 외부 모듈의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-187">A list of external modules that this module is depends on.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-188">-FileList</span><span class="sxs-lookup"><span data-stu-id="11a0d-188">-FileList</span></span>

<span data-ttu-id="11a0d-189">모듈에 포함된 모든 항목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-189">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="11a0d-190">이 키는 모듈 인벤토리 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-190">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="11a0d-191">키에 나열 된 파일은 모듈이 게시 될 때 포함 되지만 모든 기능을 자동으로 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-191">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-192">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="11a0d-192">-FormatsToProcess</span></span>

<span data-ttu-id="11a0d-193">`.ps1xml`모듈을 가져올 때 실행 되는 서식 파일 ()을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-193">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="11a0d-194">모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-194">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="11a0d-195">형식 지정 파일의 범위는 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-195">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-196">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="11a0d-196">-FunctionsToExport</span></span>

<span data-ttu-id="11a0d-197">모듈이 내보내는 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-197">Specifies the functions that the module exports.</span></span> <span data-ttu-id="11a0d-198">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-198">Wildcards are permitted.</span></span>

<span data-ttu-id="11a0d-199">이 매개 변수를 사용하여 모듈이 내보내는 함수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-199">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="11a0d-200">내보낸 별칭 목록에서 함수를 제거할 수 있지만 목록에 함수를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-200">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="11a0d-201">이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **Functionstoexport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 함수를 매니페스트에서 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-201">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="11a0d-202">-Guid</span><span class="sxs-lookup"><span data-stu-id="11a0d-202">-Guid</span></span>

<span data-ttu-id="11a0d-203">모듈의 고유 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-203">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="11a0d-204">**GUID** 를 사용 하 여 이름이 같은 모듈을 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-204">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="11a0d-205">이 매개 변수를 생략 하면에서 `New-ModuleManifest` 매니페스트에 **guid** 키를 만들고 값에 대 한 **guid** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-205">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="11a0d-206">PowerShell에서 새 **GUID** 를 만들려면를 입력 `[guid]::NewGuid()` 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-206">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-207">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="11a0d-207">-HelpInfoUri</span></span>

<span data-ttu-id="11a0d-208">모듈에 대 한 HelpInfo XML 파일의 인터넷 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-208">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="11a0d-209">**Http** 또는 **https** 로 시작 하는 URI (Uniform resource Identifier)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-209">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="11a0d-210">HelpInfo XML 파일은 PowerShell 3.0에 도입 된 업데이트할 수 있는 도움말 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-210">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="11a0d-211">이 파일에는 모듈에 대한 다운로드 가능한 도움말 파일의 위치 및 지원되는 각 로캘에 대한 최신 도움말 파일의 버전 번호 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-211">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="11a0d-212">업데이트할 수 있는 도움말에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-212">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="11a0d-213">HelpInfo XML 파일에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-213">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="11a0d-214">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-214">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="11a0d-215">-IconUri</span><span class="sxs-lookup"><span data-stu-id="11a0d-215">-IconUri</span></span>

<span data-ttu-id="11a0d-216">모듈에 대 한 아이콘의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-216">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="11a0d-217">지정 된 아이콘은 모듈에 대 한 갤러리 웹 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-217">The specified icon is displayed on the gallery web page for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-218">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="11a0d-218">-LicenseUri</span></span>

<span data-ttu-id="11a0d-219">모듈에 대 한 라이선스 조건의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-219">Specifies the URL of licensing terms for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-220">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="11a0d-220">-ModuleList</span></span>

<span data-ttu-id="11a0d-221">이 모듈에 포함된 모든 모듈을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-221">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="11a0d-222">각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-222">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="11a0d-223">해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-223">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="11a0d-224">매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-224">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="11a0d-225">이 키는 모듈 인벤토리 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-225">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="11a0d-226">이 키의 값에 나열 된 모듈은 자동으로 처리 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-226">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-227">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="11a0d-227">-ModuleVersion</span></span>

<span data-ttu-id="11a0d-228">모듈의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-228">Specifies the module's version.</span></span>

<span data-ttu-id="11a0d-229">이 매개 변수는 필수는 아니지만 매니페스트에 **ModuleVersion** 키가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-229">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="11a0d-230">이 매개 변수를 생략 하면에서 `New-ModuleManifest` 1.0 값을 사용 하 여 **ModuleVersion** 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-230">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-231">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="11a0d-231">-NestedModules</span></span>

<span data-ttu-id="11a0d-232">`.psm1` `.dll` 모듈의 세션 상태로 가져올 스크립트 모듈 () 및 이진 모듈 ()을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-232">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="11a0d-233">**NestedModules** 키의 파일은 값에 나열 된 순서 대로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-233">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="11a0d-234">각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-234">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="11a0d-235">해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-235">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="11a0d-236">매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-236">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="11a0d-237">일반적으로 중첩 모듈에는 내부 처리를 위해 루트 모듈에 필요한 명령이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-237">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="11a0d-238">기본적으로 중첩 모듈의 명령은 모듈의 세션 상태에서 호출자의 세션 상태로 내보내지고 루트 모듈은 내보내는 명령을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-238">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="11a0d-239">예를 들어 `Export-ModuleMember` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-239">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="11a0d-240">모듈 세션 상태의 중첩 모듈은 루트 모듈에서 사용할 수 있지만 `Get-Module` 호출자 세션 상태의 명령에 의해 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-240">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="11a0d-241">`.ps1` **NestedModules** 키에 나열 된 스크립트 ()는 호출자의 세션 상태가 아닌 모듈의 세션 상태에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-241">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="11a0d-242">호출자의 세션 상태에서 스크립트를 실행하려면 매니페스트의 **ScriptsToProcess** 키 값에 스크립트 파일 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-242">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-243">-PassThru</span><span class="sxs-lookup"><span data-stu-id="11a0d-243">-PassThru</span></span>

<span data-ttu-id="11a0d-244">결과 모듈 매니페스트를 콘솔에 기록 하 고 파일을 만듭니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-244">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="11a0d-245">기본적으로이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-245">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="11a0d-246">-Path</span><span class="sxs-lookup"><span data-stu-id="11a0d-246">-Path</span></span>

<span data-ttu-id="11a0d-247">새 모듈 매니페스트의 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-247">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="11a0d-248">파일 이름 확장명을 사용 하는 경로 및 파일 이름 (예:)을 입력 `.psd1` `$pshome\Modules\MyModule\MyModule.psd1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-248">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="11a0d-249">**Path** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-249">The **Path** parameter is required.</span></span>

<span data-ttu-id="11a0d-250">기존 파일에 대 한 경로를 지정 하는 경우 `New-ModuleManifest` 파일에 읽기 전용 특성이 없는 경우는 경고 없이 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-250">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="11a0d-251">매니페스트는 모듈 디렉터리에 있어야 하며 매니페스트 파일 이름은 모듈 디렉터리 이름과 동일 해야 하지만 파일 이름 확장명을 사용 해야 합니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-251">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="11a0d-252">`$PSHOME` `$HOME` **경로** 매개 변수 값에 대 한 프롬프트에 응답 하 여 또는와 같은 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-252">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="11a0d-253">변수를 사용하려면 명령에 **Path** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-253">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-254">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="11a0d-254">-PowerShellHostName</span></span>

<span data-ttu-id="11a0d-255">모듈에 필요한 PowerShell 호스트 프로그램의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-255">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="11a0d-256">호스트 프로그램의 이름 (예: **Windows PowerShell ISE host** 또는 **ConsoleHost** )을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-256">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="11a0d-257">와일드 카드는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-257">Wildcards aren't permitted.</span></span>

<span data-ttu-id="11a0d-258">호스트 프로그램의 이름을 찾으려면 프로그램에서을 입력 `$Host.Name` 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-258">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="11a0d-259">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="11a0d-259">-PowerShellHostVersion</span></span>

<span data-ttu-id="11a0d-260">모듈에서 작동 하는 PowerShell 호스트 프로그램의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-260">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="11a0d-261">버전 번호를 입력하세요(예: 1.1).</span><span class="sxs-lookup"><span data-stu-id="11a0d-261">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-262">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="11a0d-262">-PowerShellVersion</span></span>

<span data-ttu-id="11a0d-263">이 모듈에서 작동 하는 PowerShell의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-263">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="11a0d-264">예를 들어 매개 변수의 값으로 1.0, 2.0 또는 3.0을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-264">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-265">-시험판</span><span class="sxs-lookup"><span data-stu-id="11a0d-265">-Prerelease</span></span>

<span data-ttu-id="11a0d-266">이 모듈의 시험판 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-266">Prerelease string of this module.</span></span> <span data-ttu-id="11a0d-267">시험판 문자열을 추가 하면 모듈이 시험판 버전으로 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-267">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="11a0d-268">모듈이 PowerShell 갤러리에 게시 될 때이 데이터는 시험판 패키지를 식별 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-268">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="11a0d-269">갤러리에서 시험판 패키지를 얻으려면 PowerShellGet 명령,, 및와 함께 **allowprerelease** 매개 변수를 사용 해야 합니다 `Find-Module` `Install-Module` `Update-Module` `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-269">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

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

### <span data-ttu-id="11a0d-270">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="11a0d-270">-PrivateData</span></span>

<span data-ttu-id="11a0d-271">모듈을 가져올 때 모듈에 전달 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-271">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-272">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="11a0d-272">-ProcessorArchitecture</span></span>

<span data-ttu-id="11a0d-273">모듈에 필요한 프로세서 아키텍처를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-273">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="11a0d-274">유효한 값은 x86, AMD64, IA64, MSIL 및 None (알 수 없음 또는 지정 되지 않음)입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-274">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-275">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="11a0d-275">-ProjectUri</span></span>

<span data-ttu-id="11a0d-276">이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-276">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-277">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="11a0d-277">-ReleaseNotes</span></span>

<span data-ttu-id="11a0d-278">릴리스 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-278">Specifies release notes.</span></span>

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

### <span data-ttu-id="11a0d-279">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="11a0d-279">-RequiredAssemblies</span></span>

<span data-ttu-id="11a0d-280">`.dll`모듈에 필요한 어셈블리 () 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-280">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="11a0d-281">어셈블리 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-281">Enter the assembly file names.</span></span>
<span data-ttu-id="11a0d-282">PowerShell은 형식 또는 형식을 업데이트 하거나, 중첩 모듈을 가져오거나, **RootModule** 키 값에 지정 된 모듈 파일을 가져오기 전에 지정 된 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-282">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="11a0d-283">이 매개 변수를 사용하면 어셈블리가 **NestedModules** 키에 이진 모듈로 나열되는 경우에도 **FormatsToProcess** 또는 **TypesToProcess** 키에 나열된 형식 지정 파일이나 유형 파일을 업데이트하기 위해 로드해야 하는 어셈블리를 포함하여 모듈에 필요한 모든 어셈블리를 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-283">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-284">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="11a0d-284">-RequiredModules</span></span>

<span data-ttu-id="11a0d-285">전역 세션 상태여야 하는 모듈을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-285">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="11a0d-286">필수 모듈이 전역 세션 상태가 아닌 경우 PowerShell에서 해당 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-286">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="11a0d-287">필수 모듈을 사용할 수 없는 경우 `Import-Module` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-287">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="11a0d-288">각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-288">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="11a0d-289">해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-289">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="11a0d-290">매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-290">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="11a0d-291">PowerShell 2.0에서는 `Import-Module` 필요한 모듈을 자동으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-291">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="11a0d-292">필수 모듈이 전역 세션 상태에 있는지만 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-292">It just verifies that the required modules are in the global session state.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-293">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="11a0d-293">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="11a0d-294">모듈에서 설치, 업데이트 및 저장에 대 한 명시적 사용자 동의가 필요한 지 여부를 나타내는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-294">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-295">-RootModule</span><span class="sxs-lookup"><span data-stu-id="11a0d-295">-RootModule</span></span>

<span data-ttu-id="11a0d-296">모듈의 기본 또는 루트 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-296">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="11a0d-297">스크립트 ( `.ps1` ), 스크립트 모듈 ( `.psm1` ), 모듈 매니페스트 ( `.psd1` ), 어셈블리 ( `.dll` ), cmdlet 정의 XML 파일 ( `.cdxml` ) 또는 워크플로 ( `.xaml` )의 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-297">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="11a0d-298">모듈을 가져오는 경우 루트 모듈 파일에서 내보낸 멤버를 호출자의 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-298">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="11a0d-299">모듈에 매니페스트 파일이 있고 루트 파일이 **RootModule** 키에 지정 되지 않은 경우 매니페스트는 모듈의 주 파일이 되 고 모듈은 매니페스트 모듈이 됩니다 (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="11a0d-299">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="11a0d-300">`.psm1`매니페스트가 포함 된 모듈의 또는 파일에서 멤버를 내보내려면 `.dll` 해당 파일의 이름을 매니페스트의 **RootModule** 또는 **NestedModules** 키 값에 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-300">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="11a0d-301">그렇지 않으면 해당 멤버를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-301">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="11a0d-302">PowerShell 2.0에서는이 키를 **ModuleToProcess** 라고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-302">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="11a0d-303">**RootModule** 매개 변수 이름 또는 해당 **ModuleToProcess** 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-303">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-304">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="11a0d-304">-ScriptsToProcess</span></span>

<span data-ttu-id="11a0d-305">`.ps1`모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 () 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-305">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="11a0d-306">로그인 스크립트를 사용하는 것처럼 이러한 스크립트를 사용하여 환경을 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-306">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="11a0d-307">모듈의 세션 상태에서 실행되는 스크립트를 지정하려면 **NestedModules** 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-307">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-308">-태그</span><span class="sxs-lookup"><span data-stu-id="11a0d-308">-Tags</span></span>

<span data-ttu-id="11a0d-309">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-309">Specifies an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-310">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="11a0d-310">-TypesToProcess</span></span>

<span data-ttu-id="11a0d-311">`.ps1xml`모듈을 가져올 때 실행 되는 형식 파일 ()을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-311">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="11a0d-312">모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-312">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="11a0d-313">형식 파일은 범위가 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-313">Because type files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-314">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="11a0d-314">-VariablesToExport</span></span>

<span data-ttu-id="11a0d-315">모듈이 내보내는 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-315">Specifies the variables that the module exports.</span></span> <span data-ttu-id="11a0d-316">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-316">Wildcards are permitted.</span></span>

<span data-ttu-id="11a0d-317">이 매개 변수를 사용하여 모듈이 내보내는 변수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-317">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="11a0d-318">내보낸 변수 목록에서 변수를 제거할 수 있지만 목록에 변수를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-318">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="11a0d-319">이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **VariablesToExport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 변수를 매니페스트에서 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-319">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="11a0d-320">-Confirm</span><span class="sxs-lookup"><span data-stu-id="11a0d-320">-Confirm</span></span>

<span data-ttu-id="11a0d-321">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-321">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-322">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="11a0d-322">-WhatIf</span></span>

<span data-ttu-id="11a0d-323">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `New-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="11a0d-323">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="11a0d-324">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-324">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="11a0d-325">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="11a0d-325">CommonParameters</span></span>

<span data-ttu-id="11a0d-326">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="11a0d-326">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="11a0d-327">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="11a0d-327">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="11a0d-328">입력</span><span class="sxs-lookup"><span data-stu-id="11a0d-328">INPUTS</span></span>

### <span data-ttu-id="11a0d-329">없음</span><span class="sxs-lookup"><span data-stu-id="11a0d-329">None</span></span>

<span data-ttu-id="11a0d-330">이 cmdlet에는 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-330">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="11a0d-331">출력</span><span class="sxs-lookup"><span data-stu-id="11a0d-331">OUTPUTS</span></span>

### <span data-ttu-id="11a0d-332">없음 또는 System.String</span><span class="sxs-lookup"><span data-stu-id="11a0d-332">None or System.String</span></span>

<span data-ttu-id="11a0d-333">기본적으로는 `New-ModuleManifest` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-333">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="11a0d-334">그러나 **PassThru** 매개 변수를 사용 하는 경우에는 모듈 매니페스트를 나타내는 **system.string** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-334">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="11a0d-335">참고</span><span class="sxs-lookup"><span data-stu-id="11a0d-335">NOTES</span></span>

<span data-ttu-id="11a0d-336">`New-ModuleManifest` Windows 및 비 Windows 플랫폼에서 실행 하면 `.psd1` **UTF8NoBOM** 로 인코딩된 모듈 매니페스트 () 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-336">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="11a0d-337">모듈 매니페스트는 대개 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-337">Module manifests are usually optional.</span></span> <span data-ttu-id="11a0d-338">그러나 모듈 매니페스트는 전역 어셈블리 캐시에 설치되는 어셈블리를 내보내는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-338">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="11a0d-339">디렉터리에서 파일을 추가 하거나 변경 하려면 `$pshome\Modules` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-339">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="11a0d-340">PowerShell 6.2부터 PowerShell은 모듈 매니페스트의 **FileList** 속성에 나열 된 모든 DLL 파일을 로드 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-340">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="11a0d-341">기본 Dll이 프로세스에서 **로드 되지 않고** , 오류는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-341">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="11a0d-342">프로세스에서 관리 되는 모든 Dll이 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-342">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="11a0d-343">이 동작은 PowerShell 7.1에서 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-343">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="11a0d-344">PowerShell 2.0에서는 모듈 매니페스트에 필요 하지 않더라도의 많은 매개 변수가 `New-ModuleManifest` 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-344">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="11a0d-345">PowerShell 3.0부터 **Path** 매개 변수만 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-345">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="11a0d-346">세션은 PowerShell 실행 환경의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-346">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="11a0d-347">세션에 하나 이상의 세션 상태가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-347">A session can have one or more session states.</span></span> <span data-ttu-id="11a0d-348">기본적으로 세션에는 하나의 전역 세션 상태만 있지만 가져온 각 모듈에 해당 세션 상태가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-348">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="11a0d-349">세션 상태를 사용하면 모듈의 명령이 전역 세션 상태에 영향을 주지 않고 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-349">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="11a0d-350">호출자의 세션 상태는 모듈을 가져오는 세션 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-350">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="11a0d-351">일반적으로 전역 세션 상태를 참조 하지만 모듈이 중첩 모듈을 가져오는 경우 호출자는 모듈이 고 호출자의 세션 상태는 모듈의 세션 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11a0d-351">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="11a0d-352">관련 링크</span><span class="sxs-lookup"><span data-stu-id="11a0d-352">RELATED LINKS</span></span>

[<span data-ttu-id="11a0d-353">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="11a0d-353">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="11a0d-354">Get-Module</span><span class="sxs-lookup"><span data-stu-id="11a0d-354">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="11a0d-355">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="11a0d-355">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="11a0d-356">New-Module</span><span class="sxs-lookup"><span data-stu-id="11a0d-356">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="11a0d-357">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="11a0d-357">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="11a0d-358">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="11a0d-358">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="11a0d-359">about_Modules</span><span class="sxs-lookup"><span data-stu-id="11a0d-359">about_Modules</span></span>](./About/about_Modules.md)
