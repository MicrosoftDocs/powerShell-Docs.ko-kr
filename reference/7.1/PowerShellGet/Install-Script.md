---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: 2be7545829ddbbb7ddad798acb82f83c0feb3db1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215690"
---
# Install-Script

## 개요
스크립트를 설치 합니다.

## SYNTAX

### NameParameterSet (기본값)

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Install-Script`Cmdlet은 리포지토리에서 스크립트 페이로드를 획득 하 고 페이로드가 유효한 PowerShell 스크립트 인지 확인 하 고 스크립트 파일을 지정 된 설치 위치에 복사 합니다.

에 대해 작동 하는 기본 리포지토리는 `Install-Script` ,, 및 cmdlet을 통해 구성할 수 `Register-PSRepository` `Set-PSRepository` `Unregister-PSRepository` `Get-PSRepository` 있습니다. 여러 리포지토리에 대해 작업 하는 경우는 `Install-Script` 오류 없이 첫 번째 리포지토리에서 지정 된 검색 조건 **(Name** , **MinimumVersion** 또는 **MaximumVersion** )과 일치 하는 첫 번째 스크립트를 설치 합니다.

## 예제

### 예제 1: 스크립트 찾기 및 설치

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

첫 번째 명령은 Local1 리포지토리에서 이라는 스크립트를 찾아 `Required-Script2` 결과를 표시 합니다.

두 번째 명령은 `Required-Script2` 스크립트를 찾은 다음 파이프라인 연산자를 사용 하 여 cmdlet에 전달 하 여 `Install-Script` 설치 합니다.

세 번째 명령은 cmdlet을 사용 하 여 `Get-Command` `Required-Script2` 를 가져온 다음 결과를 표시 합니다.

네 번째 명령은 cmdlet을 사용 하 여 `Get-InstalledScript` 결과를 가져오고 `Required-Script2` 표시 합니다.

다섯 번째 명령은 `Required-Script2` 파이프라인 연산자를 가져와 cmdlet에 전달 하 여 `Format-List` 출력 형식을 지정 합니다.

### 예 2: AllUsers 범위를 사용 하 여 스크립트 설치

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

첫 번째 명령은 이라는 스크립트를 설치 `Required-Script3` 하 고이를 AllUsers 범위에 할당 합니다.

두 번째 명령은 설치 된 스크립트를 가져오고 `Required-Script3` 해당 스크립트에 대 한 정보를 표시 합니다.

세 번째 명령은 `Required-Script3` 파이프라인 연산자를 가져와 cmdlet에 전달 하 여 `Format-List` 출력 형식을 지정 합니다.

### 예제 3: 스크립트 및 해당 종속성 설치

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

첫 번째 명령은 Local1 리포지토리에서 이라는 스크립트 `Script-WithDependencies2` 와 해당 종속성을 찾아 결과를 표시 합니다.

두 번째 명령은를 설치 `Script-WithDependencies2` 합니다.

세 번째 명령은 스크립트 cmdlet을 사용 하 여 `Get-InstalledScript` 설치 된 스크립트를 가져오고 결과를 표시 합니다.

네 번째 명령은 cmdlet을 사용 하 여 `Get-InstalledModule` 설치 된 모듈을 가져오고 결과를 표시 합니다.

다섯 번째 명령은 cmdlet을 사용 하 여 `Find-Script` 이름이로 시작 하 `Required-Script` 고 결과를 표시 하는 스크립트를 찾습니다.

여섯 번째 명령은 Local1 리포지토리에서 이름이로 시작 하는 스크립트를 설치 합니다 `Required-Script` .

최종 명령은 설치 된 스크립트를 가져오고 결과를 표시 합니다.

## PARAMETERS

### -AcceptLicense

모듈에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.

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

### -AllowPrerelease

시험판으로 표시 된 스크립트를 설치할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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

### -Credential

지정 된 패키지 공급자나 원본에 대 한 스크립트를 설치할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### -InputObject

파이프라인 입력에 사용 됩니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

설치할 단일 스크립트의 최대 버전을 지정 합니다. 여러 스크립트를 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다. **MaximumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

설치할 단일 스크립트의 최소 버전을 지정 합니다. 여러 스크립트를 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다. **MinimumVersion** 및 **RequiredVersion** 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

설치할 스크립트의 이름 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoPathUpdate

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

### -PassThru

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

### -프록시

인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -리포지토리

Cmdlet에 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` . 기본값은 등록 된 모든 리포지토리입니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

설치할 스크립트의 정확한 버전 번호를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -범위

스크립트의 설치 범위를 지정합니다.
유효한 값은 AllUsers 및 CurrentUser입니다.

AllUsers 범위를 사용 하면 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 모듈을 설치할 수 있습니다 `$env:ProgramFiles\WindowsPowerShell\Scripts` .

CurrentUser 범위를 사용 하면 모듈을에만 설치할 수 `$home\Documents\WindowsPowerShell\Scripts` 있으므로 모듈을 현재 사용자만 사용할 수 있습니다.

**범위** 를 정의 하지 않으면 현재 세션에 따라 기본값이 설정 됩니다.

- 관리자 권한 PowerShell 세션의 경우 기본 **범위** 는 AllUsers로 설정 됩니다.
- [PowerShellGet 버전 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) 이상에서 관리자가 아닌 PowerShell 세션의 경우 **범위** 는 CurrentUser입니다.
- PowerShellGet 버전 1.6.7 및 이전 버전의 관리자가 아닌 PowerShell 세션의 경우 **범위가** 정의 되지 않고 `Install-Module` 실패 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

### System.web. PSObject []

### System.String

### System.Uri

### System.object. PSCredential

## 출력

### System.Object

## 참고

## 관련 링크

[Find-Script](Find-Script.md)

[Publish-Script](Publish-Script.md)

[Save-Script](Save-Script.md)

[Uninstall-Script](Uninstall-Script.md)

[Update-Script](Update-Script.md)

