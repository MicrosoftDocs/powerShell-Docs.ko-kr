---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: e393916f00e3670cd1ed3b5772bf165c43cc3a2f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343952"
---
# New-PSSessionConfigurationFile

## 개요
세션 구성을 정의하는 파일을 만듭니다.

## SYNTAX

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## 설명

Cmdlet은 세션 구성 `New-PSSessionConfigurationFile` 및 세션 구성을 사용 하 여 만든 세션의 환경을 정의 하는 설정 파일을 만듭니다.
세션 구성에서이 파일을 사용 하려면 또는 cmdlet의 **Path** 매개 변수를 사용 합니다 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` .

에서 만드는 세션 구성 파일은 `New-PSSessionConfigurationFile` 세션 구성 속성 및 값의 해시 테이블을 포함 하는 사람이 읽을 수 있는 텍스트 파일입니다. 파일에는 파일 `.pssc` 이름 확장명이 있습니다.

`New-PSSessionConfigurationFile` **Path** 매개 변수를 제외 하 고의 모든 매개 변수는 선택 사항입니다.
매개 변수를 생략하면 매개 변수 설명에 표시된 경우를 제외하고 세션 구성 파일의 해당 키가 주석으로 처리됩니다.

끝점 이라고 하는 세션 구성은 컴퓨터에 연결 하는 PowerShell **세션 (pssession** )에 대 한 환경을 정의 하는 로컬 컴퓨터의 설정 모음입니다. 모든 **pssession은 세션 구성을** 사용 합니다. 특정 세션 구성을 지정 하려면 cmdlet과 같이 세션을 만드는 cmdlet의 **ConfigurationName** 매개 변수를 사용 합니다 `New-PSSession` .

session configuration file을 사용하면 복잡한 스크립트나 코드 어셈블리 없이 세션 구성을 쉽게 정의할 수 있습니다. 파일의 설정은 세션 구성의 선택적 시작 스크립트 및 어셈블리와 함께 사용 됩니다.

세션 구성 및 세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md) 및 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

## 예제

### 예제 1: NoLanguage 세션 만들기 및 사용

이 예제에서는를 만들고 언어 세션이 없는 세션을 사용 하는 방법을 보여 줍니다.

단계는 다음과 같습니다.

1. 새 구성 파일을 만듭니다.
1. 구성을 등록 합니다.
1. 구성을 사용 하는 새 세션을 만듭니다.
1. 해당 새 세션에서 명령을 실행 합니다.

이 예제의 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다. Cmdlet을 실행 하려면이 옵션을 선택 해야 `Register-PSSessionConfiguration` 합니다.

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

이 예에서는 `Invoke-Command` **LanguageMode** 이 **nolanguage** 로 설정 되어 있으므로이 실패 합니다.

### 예제 2: RestrictedLanguage 세션 만들기 및 사용

이 예제에서는를 만들고 언어 세션이 없는 세션을 사용 하는 방법을 보여 줍니다.

단계는 다음과 같습니다.

1. 새 구성 파일을 만듭니다.
1. 구성을 등록 합니다.
1. 구성을 사용 하는 새 세션을 만듭니다.
1. 해당 새 세션에서 명령을 실행 합니다.

이 예제의 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다. Cmdlet을 실행 하려면이 옵션을 선택 해야 `Register-PSSessionConfiguration` 합니다.

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

이 예제에서 LanguageMode는 `Invoke-Command` **RestrictedLanguage** 로 설정 **LanguageMode** 되어 있으므로 성공 합니다.

### 예 3: 세션 구성 파일 변경

이 예에서는 "ITTasks" 라는 기존 세션에서 사용 되는 세션 구성 파일을 변경 하는 방법을 보여 줍니다. 이전에는 이러한 세션에 핵심 모듈과 내부 **Ittasks** 모듈도 있었습니다. 관리자는 ITTasks 세션 구성을 사용 하 여 만든 세션에 **PSScheduledJob** 모듈을 추가 하려고 합니다.

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

Cmdlet을 통해 `New-PSSessionConfigurationFile` 필요한 모듈을 가져오는 세션 구성 파일을 만들 수 있습니다. `Set-PSSessionConfiguration`Cmdlet은 현재 구성 파일을 새 구성 파일로 바꿉니다. 이 새 구성은 변경 후에 생성 된 새 세션에만 영향을 줍니다.
기존 "ITTasks" 세션에는 영향을 주지 않습니다.

### 예제 4: 세션 구성 파일 편집

이 예제에서는 구성 파일의 활성 세션 구성 사본을 편집하여 세션 구성을 변경하는 방법을 보여 줍니다. 구성 파일의 세션 구성 복사본을 수정 하려면 파일에 대 한 모든 권한이 있어야 합니다. 이 경우 파일에 대 한 사용 권한을 변경 해야 할 수 있습니다.

이 시나리오에서는 `Select-String` 활성 구성 파일을 편집 하 여 cmdlet에 대 한 새 별칭을 추가 하려고 합니다.

아래 예제 코드는 다음 단계를 수행 하 여 이러한 변경을 수행 합니다.

1. ITConfig 세션의 구성 파일 경로를 가져옵니다.
1. 사용자는 **Notepad.exe** 를 사용 하 여 구성 파일을 편집 하 여 **AliasDefinitions** 값을 다음과 같이 변경 합니다 `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .
1. 업데이트 된 구성 파일을 테스트 합니다.

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

에서 **Verbose** 매개 변수를 사용 `Test-PSSessionConfigurationFile` 하 여 검색 된 오류를 표시 합니다. Cmdlet은 `$True` 파일에서 오류가 검색 되지 않으면를 반환 합니다.

### 예제 5: 샘플 구성 파일 만들기

이 예에서는 `New-PSSessionConfigurationFile` 모든 cmdlet 매개 변수를 사용 하는 명령을 보여 줍니다.
이 명령은 각 매개 변수의 올바른 입력 형식을 보여 주기 위해 포함되었습니다.

결과 SampleFile.pssc가 출력에 표시됩니다.

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## PARAMETERS

### -AliasDefinitions

세션 구성을 사용하는 세션에 지정된 별칭을 추가합니다. 다음 키를 사용하여 해시 테이블을 입력합니다.

- 이름-별칭의 이름입니다. 이 키는 필수입니다.
- Value-별칭이 나타내는 명령입니다. 이 키는 필수입니다.
- Description-별칭을 설명 하는 텍스트 문자열입니다. 이 키는 선택 사항입니다.
- 옵션-별칭 옵션입니다. 이 키는 선택 사항입니다. 기본값은 **None** 입니다. 이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.

`@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

세션 구성을 사용하는 세션에 로드할 어셈블리를 지정합니다.

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

### -작성자

세션 구성 또는 구성 파일의 작성자를 지정 합니다. 기본값은 현재 사용자입니다. 이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.

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

### -CompanyName

세션 구성 또는 구성 파일을 만든 회사를 지정 합니다. 기본값은 **알 수 없음** 입니다. 이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### -저작권

세션 구성 파일의 저작권을 지정 합니다. 이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.

이 매개 변수를 생략 하면은 `New-PSSessionConfigurationFile` **Author** 매개 변수 값을 사용 하 여 저작권 설명을 생성 합니다.

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

세션 구성 또는 세션 구성 파일에 대 한 설명을 지정 합니다. 이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.

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

### -환경 변수

세션에 환경 변수를 추가합니다. 키가 환경 변수 이름이고 값이 환경 변수 값인 해시 테이블을 입력합니다.

`EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionPolicy

세션 구성을 사용하는 세션의 실행 정책을 지정합니다. 이 매개 변수를 생략 하면 세션 구성 파일의 **set-executionpolicy** 키 값이 **제한** 됩니다. PowerShell의 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about/about_Execution_Policies.md)를 참조 하세요.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

세션 구성을 사용하는 세션에서 실행되는 형식 지정 파일(.ps1xml)을 지정합니다.
이 매개 변수 값은 형식 지정 파일의 전체 또는 절대 경로 여야 합니다.

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

### -Full

이 작업에 세션 구성 파일의 가능한 모든 구성 속성이 포함 되어 있음을 나타냅니다.

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

### -FunctionDefinitions

세션 구성을 사용하는 세션에 지정된 함수를 추가합니다. 다음 키를 사용하여 해시 테이블을 입력합니다.

- 이름-함수의 이름입니다. 이 키는 필수입니다.
- ScriptBlock-함수 본문. 스크립트 블록을 입력합니다. 이 키는 필수입니다.
- 옵션-함수 옵션입니다. 이 키는 선택 사항입니다. 기본값은 **None** 입니다. 이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.

`@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Msds-groupmanagedserviceaccount

지정 된 그룹 관리 서비스 계정의 컨텍스트에서 실행 되도록이 세션 구성을 사용 하 여 세션을 구성 합니다. 세션을 성공적으로 만들려면이 세션 구성이 등록 된 컴퓨터에 gMSA 암호를 요청할 수 있는 권한이 있어야 합니다. 이 필드는 **RunAsVirtualAccount** 매개 변수와 함께 사용할 수 없습니다.

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

### -Guid

세션 구성 파일의 고유 식별자를 지정합니다. 이 매개 변수를 생략 하면는 `New-PSSessionConfigurationFile` 파일에 대 한 GUID를 생성 합니다. PowerShell에서 새 GUID를 만들려면를 입력 `New-Guid` 합니다.

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LanguageMode

이 세션 구성을 사용 하는 세션에서 허용 되는 PowerShell 언어 요소를 결정 합니다. 이 매개 변수를 사용하여 특정 사용자가 컴퓨터에서 실행할 수 있는 명령을 제한할 수 있습니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- FullLanguage-모든 언어 요소가 허용 됩니다.
- ConstrainedLanguage-평가할 스크립트가 포함 된 명령은 사용할 수 없습니다. ConstrainedLanguage 모드는 Microsoft .NET Framework 형식, 개체 또는 메서드에 대한 사용자 액세스를 제한합니다.
- NoLanguage-사용자는 cmdlet 및 함수를 실행할 수 있지만 스크립트 블록, 변수 또는 연산자와 같은 언어 요소는 사용할 수 없습니다.
- RestrictedLanguage-사용자는 cmdlet 및 함수를 실행할 수 있지만,,, `$PSCulture` `$PSUICulture` `$True` `$False` 및의 허용 되는 변수를 제외 하 고는 스크립트 블록이 나 변수를 사용할 `$Null` 수 없습니다. 사용자는 기본 비교 연산자 ( `-eq` ,,)만 사용할 수 있습니다 `-gt` `-lt` . 대입문, 속성 참조 및 메서드 호출은 허용되지 않습니다.

**LanguageMode** 매개 변수의 기본값은 **SessionType** 매개 변수 값에 따라 달라집니다.

- Empty-NoLanguage
- RestrictedRemoteServer-NoLanguage
- 기본값-FullLanguage

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

세션 구성을 사용하는 세션에 자동으로 가져오는 모듈 및 스냅인을 지정합니다.

기본적으로는 **Microsoft. PowerShell. 코어** 스냅인만 원격 세션으로 가져올 수 있지만 cmdlet을 제외 하지 않는 한 사용자는 및 cmdlet을 사용 하 여 `Import-Module` `Add-PSSnapin` 모듈 및 스냅인을 세션에 추가할 수 있습니다.

이 매개 변수 값의 각 모듈이나 스냅인을 문자열 또는 해시 테이블로 나타낼 수 있습니다. 모듈 문자열은 모듈이 나 스냅인의 이름 으로만 구성 됩니다. 모듈 해시 테이블에는 **ModuleName** , **ModuleVersion** 및 **GUID** 키가 포함 될 수 있습니다. **ModuleName** 키만 필수입니다.

예를 들어 다음 값은 문자열과 해시 테이블로 구성됩니다. 순서와 관계없이 문자열과 해시 테이블의 모든 조합이 유효합니다.

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

Cmdlet의 **ModulesToImport** 매개 변수 값은 `Register-PSSessionConfiguration` 세션 구성 파일에 있는 **ModulesToImport** 키의 값 보다 우선 적용 됩니다.

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

### -MountUserDrive

PSDrive를 노출 하기 위해이 세션 구성을 사용 하는 세션을 구성 `User:` 합니다. 사용자 드라이브는 연결 하는 각 사용자에 대해 고유 하며, 파일 시스템 공급자가 노출 되지 않은 경우에도 사용자가 PowerShell 끝점 간에 데이터를 복사할 수 있도록 합니다. 사용자 드라이브 루트는 아래에 생성 됩니다 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` . 엔드포인트에 연결하는 각 사용자에 대해 `$env:USERDOMAIN_$env:USERNAME`이라는 이름으로 폴더가 만들어집니다.

사용자 드라이브의 콘텐츠는 사용자 세션에서 유지 되며 자동으로 제거 되지 않습니다. 기본적으로 사용자는 사용자 드라이브에 최대 50MB의 데이터를 저장할 수 있습니다. **UserDriveMaximumSize** 매개 변수를 사용 하 여 사용자 지정할 수 있습니다.

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

### -Path

세션 구성 파일의 경로와 파일 이름을 지정 합니다. 파일에는 `.pssc` 파일 이름 확장명이 있어야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

세션 구성을 사용 하는 세션의 PowerShell 엔진 버전을 지정 합니다. 이 매개 변수에 허용 되는 값은 2.0 및 3.0입니다. 이 매개 변수를 생략 하면 **PowerShellVersion** 키가 주석으로 처리 되 고 최신 버전의 PowerShell이 세션에서 실행 됩니다.

Cmdlet의 **PSVersion** 매개 변수 값은 `Register-PSSessionConfiguration` 세션 구성 파일에 있는 **PowerShellVersion** 키의 값 보다 우선 적용 됩니다.

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

### -RequiredGroups

이 세션 구성을 사용 하는 세션에 연결 하는 사용자에 대 한 조건부 액세스 규칙을 지정 합니다.

해시 테이블을 입력 하 여 해시 테이블, ' And ' 또는 ' Or ' 당 1 개의 키만 사용 하 여 규칙 목록을 작성 하 고, 값을 보안 그룹 이름 또는 추가 해시 테이블으로 설정 합니다.

사용자를 단일 그룹의 구성원으로 연결 해야 하는 예는 다음과 같습니다. `@{ And = 'MyRequiredGroup' }`

끝점에 액세스 하려면 사용자가 그룹 A 또는 그룹 B와 C 모두에 속해야 하는 예입니다. `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleDefinitions

보안 그룹 (또는 사용자)과 역할 기능 간의 매핑을 지정 합니다. 사용자에 게는 세션이 만들어질 때 그룹 구성원 자격에 적용 되는 모든 역할 기능에 대 한 액세스 권한이 부여 됩니다.

키가 보안 그룹의 이름이 고 값은 보안 그룹에 사용할 수 있는 역할 기능 목록을 포함 하는 해시 테이블인 해시 테이블을 입력 합니다.

`@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsVirtualAccount

컴퓨터의 (가상) 관리자 계정으로 실행 되도록이 세션 구성을 사용 하 여 세션을 구성 합니다. 이 필드는 **msds-groupmanagedserviceaccount** 매개 변수와 함께 사용할 수 없습니다.

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

### -RunAsVirtualAccountGroups

세션 구성을 사용 하는 세션이 가상 계정으로 실행 되는 경우 가상 계정과 연결 될 보안 그룹을 지정 합니다. 생략 하는 경우 가상 계정은 다른 모든 컴퓨터의 도메인 컨트롤러 및 관리자 도메인 관리자에 속합니다.

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

### -SchemaVersion

세션 구성 파일 스키마의 버전을 지정합니다. 기본값은 "1.0.0.0"입니다.

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

### -ScriptsToProcess

세션 구성을 사용하는 세션에 지정된 스크립트를 추가합니다. 스크립트의 경로와 파일 이름을 입력합니다. 이 매개 변수 값은 스크립트 파일 이름의 전체 또는 절대 경로 여야 합니다.

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

### -SessionType

세션 구성을 사용하여 만들어진 세션의 유형을 지정합니다. 기본값은 Default입니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- Empty-기본적으로 세션에 모듈을 추가 하지 않습니다. 이 cmdlet의 매개 변수를 사용하여 모듈, 함수, 스크립트 및 기타 기능을 세션에 추가할 수 있습니다. 이 옵션은 선택한 명령을 추가 하 여 사용자 지정 세션을 만들 수 있도록 설계 되었습니다. 빈 세션에 명령을 추가하지 않을 경우 세션이 식으로 제한되며 세션을 사용하지 못할 수도 있습니다.
- 기본값-세션에 Microsoft. PowerShell 핵심 모듈을 추가 합니다. 이 모듈에는 `Import-Module` 이 cmdlet을 명시적으로 금지 하지 않는 한 사용자가 다른 모듈을 가져오는 데 사용할 수 있는 cmdlet이 포함 되어 있습니다.
- RestrictedRemoteServer. 에는,,,,, `Exit-PSSession` `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` 및와 `Select-Object` 같은 프록시 함수만 포함 됩니다.
  이 cmdlet의 매개 변수를 사용하여 모듈, 함수, 스크립트 및 기타 기능을 세션에 추가할 수 있습니다.

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TranscriptDirectory

이 세션 구성을 사용 하 여 세션에 대 한 세션 기록을 저장할 디렉터리를 지정 합니다.

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

### -TypesToProcess

`.ps1xml`세션 구성을 사용 하는 세션에 지정 된 형식 파일을 추가 합니다. 유형 파일 이름을 입력 합니다. 이 매개 변수 값은 형식 파일 이름의 전체 또는 절대 경로 여야 합니다.

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

### -UserDriveMaximumSize

이 세션 구성을 사용 하는 세션에 노출 되는 사용자 드라이브의 최대 크기를 지정 합니다.
생략 하는 경우 각 드라이브 루트의 기본 크기는 `User:` 50MB입니다.

이 매개 변수는 **MountUserDrive** 와 함께 사용 해야 합니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

세션 구성을 사용하는 세션에 지정된 변수를 추가합니다. 다음 키를 사용하여 해시 테이블을 입력합니다.

- 이름-변수의 이름입니다. 이 키는 필수입니다.
- 값-변수 값입니다. 이 키는 필수입니다.
- 옵션-변수 옵션입니다. 이 키는 선택 사항입니다. 기본값은 **None** 입니다. 이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.

`@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`

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

### -VisibleAliases

세션의 별칭을 이 매개 변수 값에 지정된 별칭 및 **AliasDefinition** 매개 변수에 정의한 별칭으로 제한합니다. 와일드카드 문자가 지원됩니다. 기본적으로 PowerShell 엔진에서 정의한 모든 별칭과 모듈에서 내보낸 모든 별칭이 세션에 표시 됩니다.

`VisibleAliases='gcm', 'gp'`

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.

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

### -VisibleCmdlets

세션의 cmdlet을 이 매개 변수 값에 지정된 cmdlet으로 제한합니다. 와일드 카드 문자 및 모듈 정규화 된 이름이 지원 됩니다.

기본적으로 세션의 모듈에서 내보낸 모든 cmdlet이 세션에 표시됩니다. **SessionType** 및 **ModulesToImport** 매개 변수를 사용하여 세션으로 가져올 모듈과 스냅인을 결정할 수 있습니다. **ModulesToImport** 에서 cmdlet을 노출 하는 모듈이 없으면 적절 한 모듈이 자동 로드 됩니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.

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

### -VisibleExternalCommands

세션에서 실행할 수 있는 외부 이진 파일, 스크립트 및 명령을이 매개 변수 값에 지정 된 것으로 제한 합니다. 와일드카드 문자가 지원됩니다.

기본적으로 세션에는 외부 명령이 표시 되지 않습니다.

**표시** 되는 매개 변수가 세션 구성 파일인 PowerShell에 포함 된 경우 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.

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

### -VisibleFunctions

세션의 함수를 이 매개 변수 값에 지정된 함수 및 **FunctionDefinition** 매개 변수에 정의한 함수로 제한합니다. 와일드카드 문자가 지원됩니다.

기본적으로 세션의 모듈에서 내보낸 모든 함수가 세션에 표시됩니다. **SessionType** 및 **ModulesToImport** 매개 변수를 사용하여 세션으로 가져올 모듈과 스냅인을 결정할 수 있습니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

세션의 PowerShell 공급자를이 매개 변수 값에 지정 된 공급자로 제한 합니다.
와일드카드 문자가 지원됩니다.

기본적으로 세션의 모듈에서 내보낸 모든 공급자가 세션에 표시됩니다. **SessionType** 및 **ModulesToImport** 매개 변수를 사용 하 여 세션으로 가져올 모듈을 결정 합니다.

**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

개체를이 cmdlet으로 파이프 할 수는 없습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

- **VisibleCmdlets** 및 **VisibleProviders** 와 같은 매개 변수는 항목을 세션으로 가져오지 않습니다. 대신, 세션으로 가져온 항목 중에서 선택합니다. 예를 들어 **VisibleProviders** 매개 변수 값이 인증서 공급자 이지만 **ModulesToImport** 매개 변수는 인증서 공급자를 포함 하는 **Microsoft. PowerShell. Security** 모듈을 지정 하지 않으면 세션에 인증서 공급자가 표시 되지 않습니다.
- `New-PSSessionConfigurationFile`**path** 매개 변수에 지정 하는 경로에 .psc 파일 이름 확장명을 가진 세션 구성 파일을 만듭니다. 세션 구성 파일을 사용 하 여 세션 구성을 만드는 경우 `Register-PSSessionConfiguration` cmdlet은 구성 파일을 복사 하 고 파일의 활성 복사본을 디렉터리의 **sessionconfig** 하위 디렉터리에 저장 `$PSHOME` 합니다.

  세션 구성의 **Configfilepath** 속성에는 활성 세션 구성 파일의 정규화 된 경로가 포함 되어 있습니다. 언제 든 `$PSHOME` 지 모든 텍스트 편집기를 사용 하 여 디렉터리의 활성 구성 파일을 수정할 수 있습니다. 변경 내용은 세션 구성을 사용하는 모든 새 세션에 영향을 주지만 기존 세션에는 영향을 주지 않습니다.

  편집 된 세션 구성 파일을 사용 하기 전에 cmdlet을 사용 `Test-PSSessionConfigurationFile` 하 여 구성 파일 항목이 유효한 지 확인 합니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
