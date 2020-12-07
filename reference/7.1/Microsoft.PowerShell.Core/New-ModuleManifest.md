---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 5fbd197f6c22de0ca50b4d2b6b76a914b85f7120
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239774"
---
# New-ModuleManifest

## 개요
새 모듈 매니페스트를 만듭니다.

## SYNTAX

### 모두

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

## 설명

`New-ModuleManifest`Cmdlet은 새 모듈 매니페스트 ( `.psd1` ) 파일을 만들고 해당 값을 채운 다음 지정 된 경로에 매니페스트 파일을 저장 합니다.

모듈 작성자는 이 cmdlet을 사용하여 모듈의 매니페스트를 만들 수 있습니다. 모듈 매니페스트는 `.psd1` 해시 테이블을 포함 하는 파일입니다. 해시 테이블의 키와 값은 모듈의 내용 및 특성을 설명하고, 필수 구성 요소를 정의하고, 구성 요소의 처리 방법을 결정합니다. 모듈에는 매니페스트가 필요 하지 않습니다.

`New-ModuleManifest` 일반적으로 사용 되는 모든 매니페스트 키를 포함 하는 매니페스트를 만들어 기본 출력을 매니페스트 템플릿으로 사용할 수 있습니다. 값을 추가 또는 변경 하거나이 cmdlet이 추가 하지 않는 모듈 키를 추가 하려면 결과 파일을 텍스트 편집기에서 엽니다.

**Path** 및 **PassThru** 를 제외 하 고 각 매개 변수는 모듈 매니페스트 키와 해당 값을 만듭니다.
모듈 매니페스트에서는 **ModuleVersion** 키만 필요합니다. 매개 변수 설명에 지정 된 경우를 제외 하 고, 명령에서 매개 변수를 생략 하면는 영향을 주지 `New-ModuleManifest` 않는 관련 값에 대 한 주석 문자열을 만듭니다.

PowerShell 2.0에서는 `New-ModuleManifest` 필수 매개 변수 값 외에 명령에 지정 되지 않은 일반적으로 사용 되는 매개 변수의 값을 묻는 메시지를 표시 합니다. PowerShell 3.0부터는 `New-ModuleManifest` 필요한 매개 변수 값이 지정 되지 않은 경우에만 메시지를 표시 합니다.

PowerShell 갤러리에 모듈을 게시 하려는 경우 매니페스트에 특정 속성에 대 한 값이 포함 되어 있어야 합니다. 자세한 내용은 갤러리 설명서의 [PowerShell 갤러리에 게시 된 항목에 대 한 필수 메타 데이터](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) 를 참조 하세요.

## 예제

### 예제 1-새 모듈 매니페스트 만들기

이 예제에서는 **Path** 매개 변수로 지정 된 파일에 새 모듈 매니페스트를 만듭니다.
**PassThru** 매개 변수는 출력을 파이프라인과 파일로 보냅니다.

출력은 매니페스트에 있는 모든 키의 기본값을 보여 줍니다.

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

### 예제 2-미리 채워진 설정을 사용 하 여 새 매니페스트 만들기

이 예제에서는 새 모듈 매니페스트를 만듭니다. **PowerShellVersion** 및 **AliasesToExport** 매개 변수를 사용하여 해당 매니페스트 키에 값을 추가합니다.

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### 예제 3-다른 모듈이 필요한 매니페스트 만들기

이 예에서는 문자열 형식을 사용 하 여 **BitsTransfer** 모듈의 이름을 지정 하 고 해시 테이블 형식을 사용 하 여 이름, **GUID** 및 **PSScheduledJob** 모듈의 버전을 지정 합니다.

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

이 예에서는 **Modulelist** , **RequiredModules** 및 **NestedModules** 매개 변수의 문자열 및 해시 테이블 형식을 사용 하는 방법을 보여 줍니다. 동일한 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.

### 예제 4-업데이트할 수 있는 도움말을 지 원하는 매니페스트 만들기

이 예제에서는 **HelpInfoUri** 매개 변수를 사용 하 여 모듈 매니페스트에 **HelpInfoUri** 키를 만듭니다. 매개 변수 및 키의 값은 **http** 또는 **https** 로 시작 해야 합니다. 이 값은 업데이트할 수 있는 도움말 시스템에 모듈에 대한 HelpInfo XML 업데이트할 수 있는 도움말 정보 파일이 있는 위치를 알려줍니다.

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

업데이트할 수 있는 도움말에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.
HelpInfo XML 파일에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.

### 예 5-모듈 정보 가져오기

이 예제에서는 모듈의 구성 값을 가져오는 방법을 보여 줍니다. 모듈 매니페스트의 값은 module 개체의 속성 값에 반영 됩니다.

`Get-Module`Cmdlet은 **List** 매개 변수를 사용 하 여 **Microsoft. PowerShell 진단** 모듈을 가져오는 데 사용 됩니다. 이 명령은 모듈을 cmdlet에 전송 `Format-List` 하 여 모듈 개체의 모든 속성과 값을 표시 합니다.

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

## PARAMETERS

### -AliasesToExport

모듈이 내보내는 별칭을 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용하여 모듈이 내보내는 별칭을 제한할 수 있습니다. 내보낸 별칭 목록에서 별칭을 제거할 수 있지만 목록에 별칭을 추가할 수는 없습니다.

이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **AliasesToExport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 별칭을 매니페스트에서 내보냅니다.

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

### -작성자

모듈 작성자를 지정합니다.

이 매개 변수를 생략 하면에서 `New-ModuleManifest` 현재 사용자의 이름으로 **Author** 키를 만듭니다.

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

### -CmdletsToExport

모듈이 내보내는 cmdlet을 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용하여 모듈이 내보내는 cmdlet을 제한할 수 있습니다. 이 cmdlet은 내보낸 cmdlet 목록에서 cmdlet을 제거할 수 있지만 목록에 cmdlet을 추가할 수는 없습니다.

이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **Cmdletstoexport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 cmdlet을 매니페스트에서 내보냅니다.

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

### -CompanyName

모듈을 만든 회사나 공급업체를 식별합니다.

이 매개 변수를 생략 하면는 `New-ModuleManifest` "Unknown" 값을 사용 하 여 **CompanyName** 키를 만듭니다.

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

### -CompatiblePSEditions

모듈의 호환 되는 Pseditions가를 지정 합니다. PSEdition에 대 한 자세한 내용은 [호환 되는 PowerShell 버전이 있는 모듈](/powershell/scripting/gallery/concepts/module-psedition-support)을 참조 하세요.

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

### -저작권

모듈의 저작권 정보를 지정합니다.

이 매개 변수를 생략 하면 `New-ModuleManifest` 는 값을 갖는 **저작권** 키를 만듭니다 `(c) <year> <username>. All rights reserved.` `<year>` . 여기서는 현재 연도이 고 `<username>` 은 **Author** 키의 값입니다.

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

### -DefaultCommandPrefix

세션으로 가져올 때 모듈에 있는 모든 명령의 명사 앞에 추가할 접두사를 지정 합니다. 접두사 문자열을 입력합니다. 접두사는 사용자 세션에서 명령 이름 충돌을 방지합니다.

모듈 사용자는 cmdlet의 **prefix** 매개 변수를 지정 하 여이 접두사를 재정의할 수 있습니다 `Import-Module` .

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### -Description

모듈의 내용을 설명합니다.

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

### -DotNetFrameworkVersion

모듈에 필요한 Microsoft .NET Framework의 최소 버전을 지정합니다.

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

### -DscResourcesToExport

모듈에서 내보내는 DSC (Desired State Configuration) 리소스를 지정 합니다. 와일드카드가 지원됩니다.

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

### -ExternalModuleDependencies

이 모듈이 종속 된 외부 모듈의 목록입니다.

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

### -FileList

모듈에 포함된 모든 항목을 지정합니다.

이 키는 모듈 인벤토리 역할을 합니다. 키에 나열 된 파일은 모듈이 게시 될 때 포함 되지만 모든 기능을 자동으로 내보내지 않습니다.

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

### -FormatsToProcess

`.ps1xml`모듈을 가져올 때 실행 되는 서식 파일 ()을 지정 합니다.

모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-FormatData` .
형식 지정 파일의 범위는 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.

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

### -FunctionsToExport

모듈이 내보내는 함수를 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용하여 모듈이 내보내는 함수를 제한할 수 있습니다. 내보낸 별칭 목록에서 함수를 제거할 수 있지만 목록에 함수를 추가할 수는 없습니다.

이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **Functionstoexport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 함수를 매니페스트에서 내보냅니다.

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

### -Guid

모듈의 고유 식별자를 지정합니다. **GUID** 를 사용 하 여 이름이 같은 모듈을 구분할 수 있습니다.

이 매개 변수를 생략 하면에서 `New-ModuleManifest` 매니페스트에 **guid** 키를 만들고 값에 대 한 **guid** 를 생성 합니다.

PowerShell에서 새 **GUID** 를 만들려면를 입력 `[guid]::NewGuid()` 합니다.

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

### -HelpInfoUri

모듈에 대 한 HelpInfo XML 파일의 인터넷 주소를 지정 합니다. **Http** 또는 **https** 로 시작 하는 URI (Uniform resource Identifier)를 입력 합니다.

HelpInfo XML 파일은 PowerShell 3.0에 도입 된 업데이트할 수 있는 도움말 기능을 지원 합니다. 이 파일에는 모듈에 대한 다운로드 가능한 도움말 파일의 위치 및 지원되는 각 로캘에 대한 최신 도움말 파일의 버전 번호 정보가 포함되어 있습니다.

업데이트할 수 있는 도움말에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.
HelpInfo XML 파일에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조 하세요.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### -IconUri

모듈에 대 한 아이콘의 URL을 지정 합니다. 지정 된 아이콘은 모듈에 대 한 갤러리 웹 페이지에 표시 됩니다.

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

### -LicenseUri

모듈에 대 한 라이선스 조건의 URL을 지정 합니다.

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

### -ModuleList

이 모듈에 포함된 모든 모듈을 나열합니다.

각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다. 해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다. 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.

이 키는 모듈 인벤토리 역할을 합니다. 이 키의 값에 나열 된 모듈은 자동으로 처리 되지 않습니다.

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

### -ModuleVersion

모듈의 버전을 지정 합니다.

이 매개 변수는 필수는 아니지만 매니페스트에 **ModuleVersion** 키가 필요 합니다. 이 매개 변수를 생략 하면에서 `New-ModuleManifest` 1.0 값을 사용 하 여 **ModuleVersion** 키를 만듭니다.

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

### -NestedModules

`.psm1` `.dll` 모듈의 세션 상태로 가져올 스크립트 모듈 () 및 이진 모듈 ()을 지정 합니다. **NestedModules** 키의 파일은 값에 나열 된 순서 대로 실행 됩니다.

각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다. 해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다. 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.

일반적으로 중첩 모듈에는 내부 처리를 위해 루트 모듈에 필요한 명령이 들어 있습니다.
기본적으로 중첩 모듈의 명령은 모듈의 세션 상태에서 호출자의 세션 상태로 내보내지고 루트 모듈은 내보내는 명령을 제한할 수 있습니다. 예를 들어 `Export-ModuleMember` 명령을 사용 합니다.

모듈 세션 상태의 중첩 모듈은 루트 모듈에서 사용할 수 있지만 `Get-Module` 호출자 세션 상태의 명령에 의해 반환 되지 않습니다.

`.ps1` **NestedModules** 키에 나열 된 스크립트 ()는 호출자의 세션 상태가 아닌 모듈의 세션 상태에서 실행 됩니다. 호출자의 세션 상태에서 스크립트를 실행하려면 매니페스트의 **ScriptsToProcess** 키 값에 스크립트 파일 이름을 나열합니다.

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

### -PassThru

결과 모듈 매니페스트를 콘솔에 기록 하 고 파일을 만듭니다 `.psd1` . 기본적으로이 cmdlet은 출력을 생성 하지 않습니다.

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

### -Path

새 모듈 매니페스트의 경로와 파일 이름을 지정합니다. 파일 이름 확장명을 사용 하는 경로 및 파일 이름 (예:)을 입력 `.psd1` `$pshome\Modules\MyModule\MyModule.psd1` 합니다. **Path** 매개 변수는 필수입니다.

기존 파일에 대 한 경로를 지정 하는 경우 `New-ModuleManifest` 파일에 읽기 전용 특성이 없는 경우는 경고 없이 파일을 바꿉니다.

매니페스트는 모듈 디렉터리에 있어야 하며 매니페스트 파일 이름은 모듈 디렉터리 이름과 동일 해야 하지만 파일 이름 확장명을 사용 해야 합니다 `.psd1` .

> [!NOTE]
> `$PSHOME` `$HOME` **경로** 매개 변수 값에 대 한 프롬프트에 응답 하 여 또는와 같은 변수를 사용할 수 없습니다. 변수를 사용하려면 명령에 **Path** 매개 변수를 포함합니다.

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

### -PowerShellHostName

모듈에 필요한 PowerShell 호스트 프로그램의 이름을 지정 합니다. 호스트 프로그램의 이름 (예: **Windows PowerShell ISE host** 또는 **ConsoleHost** )을 입력 합니다. 와일드 카드는 허용 되지 않습니다.

호스트 프로그램의 이름을 찾으려면 프로그램에서을 입력 `$Host.Name` 합니다.

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

### -PowerShellHostVersion

모듈에서 작동 하는 PowerShell 호스트 프로그램의 최소 버전을 지정 합니다. 버전 번호를 입력하세요(예: 1.1).

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

### -PowerShellVersion

이 모듈에서 작동 하는 PowerShell의 최소 버전을 지정 합니다. 예를 들어 매개 변수의 값으로 1.0, 2.0 또는 3.0을 입력할 수 있습니다.

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

### -시험판

이 모듈의 시험판 문자열입니다. 시험판 문자열을 추가 하면 모듈이 시험판 버전으로 식별 됩니다. 모듈이 PowerShell 갤러리에 게시 될 때이 데이터는 시험판 패키지를 식별 하는 데 사용 됩니다. 갤러리에서 시험판 패키지를 얻으려면 PowerShellGet 명령,, 및와 함께 **allowprerelease** 매개 변수를 사용 해야 합니다 `Find-Module` `Install-Module` `Update-Module` `Save-Module` .

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

### -PrivateData

모듈을 가져올 때 모듈에 전달 되는 데이터를 지정 합니다.

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

### -ProcessorArchitecture

모듈에 필요한 프로세서 아키텍처를 지정합니다. 유효한 값은 x86, AMD64, IA64, MSIL 및 None (알 수 없음 또는 지정 되지 않음)입니다.

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

### -ProjectUri

이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.

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

### -ReleaseNotes

릴리스 정보를 지정 합니다.

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

### -RequiredAssemblies

`.dll`모듈에 필요한 어셈블리 () 파일을 지정 합니다. 어셈블리 파일 이름을 입력합니다.
PowerShell은 형식 또는 형식을 업데이트 하거나, 중첩 모듈을 가져오거나, **RootModule** 키 값에 지정 된 모듈 파일을 가져오기 전에 지정 된 어셈블리를 로드 합니다.

이 매개 변수를 사용하면 어셈블리가 **NestedModules** 키에 이진 모듈로 나열되는 경우에도 **FormatsToProcess** 또는 **TypesToProcess** 키에 나열된 형식 지정 파일이나 유형 파일을 업데이트하기 위해 로드해야 하는 어셈블리를 포함하여 모듈에 필요한 모든 어셈블리를 나열할 수 있습니다.

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

### -RequiredModules

전역 세션 상태여야 하는 모듈을 지정합니다. 필수 모듈이 전역 세션 상태가 아닌 경우 PowerShell에서 해당 모듈을 가져옵니다. 필수 모듈을 사용할 수 없는 경우 `Import-Module` 명령이 실패 합니다.

각 모듈 이름을 문자열이나 **ModuleName** 및 **ModuleVersion** 키가 포함된 해시 테이블로 입력합니다. 해시 테이블에 선택적 **GUID** 키가 포함될 수도 있습니다. 매개 변수 값에서 문자열과 해시 테이블을 결합할 수 있습니다.

PowerShell 2.0에서는 `Import-Module` 필요한 모듈을 자동으로 가져오지 않습니다. 필수 모듈이 전역 세션 상태에 있는지만 확인합니다.

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

### -RequireLicenseAcceptance

모듈에서 설치, 업데이트 및 저장에 대 한 명시적 사용자 동의가 필요한 지 여부를 나타내는 플래그입니다.

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

### -RootModule

모듈의 기본 또는 루트 파일을 지정 합니다. 스크립트 ( `.ps1` ), 스크립트 모듈 ( `.psm1` ), 모듈 매니페스트 ( `.psd1` ), 어셈블리 ( `.dll` ), cmdlet 정의 XML 파일 ( `.cdxml` ) 또는 워크플로 ( `.xaml` )의 파일 이름을 입력 합니다. 모듈을 가져오는 경우 루트 모듈 파일에서 내보낸 멤버를 호출자의 세션 상태로 가져옵니다.

모듈에 매니페스트 파일이 있고 루트 파일이 **RootModule** 키에 지정 되지 않은 경우 매니페스트는 모듈의 주 파일이 되 고 모듈은 매니페스트 모듈이 됩니다 (ModuleType = manifest).

`.psm1`매니페스트가 포함 된 모듈의 또는 파일에서 멤버를 내보내려면 `.dll` 해당 파일의 이름을 매니페스트의 **RootModule** 또는 **NestedModules** 키 값에 지정 해야 합니다. 그렇지 않으면 해당 멤버를 내보내지 않습니다.

> [!NOTE]
> PowerShell 2.0에서는이 키를 **ModuleToProcess** 라고 했습니다. **RootModule** 매개 변수 이름 또는 해당 **ModuleToProcess** 별칭을 사용할 수 있습니다.

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

### -ScriptsToProcess

`.ps1`모듈을 가져올 때 호출자의 세션 상태에서 실행 되는 스크립트 () 파일을 지정 합니다.
로그인 스크립트를 사용하는 것처럼 이러한 스크립트를 사용하여 환경을 준비할 수 있습니다.

모듈의 세션 상태에서 실행되는 스크립트를 지정하려면 **NestedModules** 키를 사용합니다.

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

### -태그

태그의 배열을 지정 합니다.

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

### -TypesToProcess

`.ps1xml`모듈을 가져올 때 실행 되는 형식 파일 ()을 지정 합니다.

모듈을 가져올 때 PowerShell에서 지정 된 파일을 사용 하 여 cmdlet을 실행 합니다 `Update-TypeData` .
형식 파일은 범위가 지정 되지 않기 때문에 세션의 모든 세션 상태에 영향을 줍니다.

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

### -VariablesToExport

모듈이 내보내는 변수를 지정합니다. 와일드카드가 지원됩니다.

이 매개 변수를 사용하여 모듈이 내보내는 변수를 제한할 수 있습니다. 내보낸 변수 목록에서 변수를 제거할 수 있지만 목록에 변수를 추가할 수는 없습니다.

이 매개 변수를 생략 하면는 `New-ModuleManifest` (all) 값을 사용 하 여 **VariablesToExport** 키를 만듭니다 `*` . 즉, 모듈에 정의 된 모든 변수를 매니페스트에서 내보냅니다.

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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

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

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `New-ModuleManifest` . Cmdlet이 실행 되지 않습니다.

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

### -ClrVersion

모듈에 필요한 Microsoft .NET Framework의 CLR(공용 언어 런타임) 최소 버전을 지정합니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에는 입력을 파이프 할 수 없습니다.

## 출력

### 없음 또는 System.String

기본적으로는 `New-ModuleManifest` 출력을 생성 하지 않습니다. 그러나 **PassThru** 매개 변수를 사용 하는 경우에는 모듈 매니페스트를 나타내는 **system.string** 개체를 생성 합니다.

## 참고

`New-ModuleManifest` Windows 및 비 Windows 플랫폼에서 실행 하면 `.psd1` **UTF8NoBOM** 로 인코딩된 모듈 매니페스트 () 파일이 만들어집니다.

모듈 매니페스트는 대개 선택 사항입니다. 그러나 모듈 매니페스트는 전역 어셈블리 캐시에 설치되는 어셈블리를 내보내는 데 필요합니다.

디렉터리에서 파일을 추가 하거나 변경 하려면 `$pshome\Modules` **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

> [!NOTE]
> PowerShell 6.2부터 PowerShell은 모듈 매니페스트의 **FileList** 속성에 나열 된 모든 DLL 파일을 로드 하려고 합니다. 기본 Dll이 프로세스에서 **로드 되지 않고** , 오류는 무시 됩니다. 프로세스에서 관리 되는 모든 Dll이 로드 됩니다. 이 동작은 PowerShell 7.1에서 제거 되었습니다.

PowerShell 2.0에서는 모듈 매니페스트에 필요 하지 않더라도의 많은 매개 변수가 `New-ModuleManifest` 필수입니다. PowerShell 3.0부터 **Path** 매개 변수만 필수입니다.

세션은 PowerShell 실행 환경의 인스턴스입니다. 세션에 하나 이상의 세션 상태가 있을 수 있습니다. 기본적으로 세션에는 하나의 전역 세션 상태만 있지만 가져온 각 모듈에 해당 세션 상태가 있습니다. 세션 상태를 사용하면 모듈의 명령이 전역 세션 상태에 영향을 주지 않고 실행될 수 있습니다.

호출자의 세션 상태는 모듈을 가져오는 세션 상태입니다. 일반적으로 전역 세션 상태를 참조 하지만 모듈이 중첩 모듈을 가져오는 경우 호출자는 모듈이 고 호출자의 세션 상태는 모듈의 세션 상태입니다.

## 관련 링크

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[모듈 가져오기](Import-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)

[Test-ModuleManifest](Test-ModuleManifest.md)

[about_Modules](./About/about_Modules.md)