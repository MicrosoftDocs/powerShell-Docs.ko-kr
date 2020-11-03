---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 506775bf4ef58244a04cb13c1cab926d112111bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217289"
---
# Install-Package

## 개요
하나 이상의 소프트웨어 패키지를 설치 합니다.

## SYNTAX

### PackageBySearch (기본값)

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### PackageByInputObject

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### NuGet: PackageBySearch

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### NuGet: PackageByInputObject

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### PowerShellGet: PackageBySearch

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### PowerShellGet: PackageByInputObject

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## 설명

`Install-Package`Cmdlet은 로컬 컴퓨터에 소프트웨어 패키지를 하나 이상 설치 합니다. 여러 소프트웨어 소스를 사용 하는 경우 `Get-PackageProvider` 및를 사용 `Get-PackageSource` 하 여 공급자에 대 한 세부 정보를 표시 합니다.

## 예제

### 예제 1: 패키지 이름으로 패키지 설치

`Install-Package`Cmdlet은 소프트웨어 패키지와 해당 종속성을 설치 합니다.

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

`Install-Package` 매개 변수를 사용 하 여 패키지 **이름** 및 **원본을** 지정 합니다. **Credential** 매개 변수는 패키지를 설치할 수 있는 권한이 있는 도메인 사용자 계정을 사용 합니다. 명령은 사용자 계정 암호를 입력 하 라는 메시지를 표시 합니다.

### 예제 2: Find-Package을 사용 하 여 패키지 설치

이 예제에서에 의해 반환 된 개체는 `Find-Package` 파이프라인으로 전송 되 고에 의해 설치 됩니다 `Install-Package` .

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

`Find-Package` 는 **이름** 및 **원본** 매개 변수를 사용 하 여 패키지를 찾습니다. 개체는 파이프라인으로 전송 되 고 `Install-Package` 로컬 컴퓨터에 패키지를 설치 합니다.

### 예제 3: 버전 범위를 지정 하 여 패키지 설치

`Install-Package` 는 **MinimumVersion** 및 **MaximumVersion** 매개 변수를 사용 하 여 소프트웨어 버전의 범위를 지정 합니다.

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

`Install-Package` 는 **이름** 및 **원본** 매개 변수를 사용 하 여 패키지를 찾습니다. **MinimumVersion** 및 **MaximumVersion** 매개 변수는 소프트웨어 버전의 범위를 지정 합니다. 범위에서 가장 높은 버전이 설치 됩니다.

## PARAMETERS

### -AcceptLicense

 **Acceptlicense** 는 설치 하는 동안 자동으로 사용권 계약에 동의 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowClobber

기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다. 설치 중인 명령과 이름이 같은 기존 명령을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

시험판으로 표시 된 패키지를 설치할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Allversions)

`Install-Package` 패키지의 사용 가능한 모든 버전을 설치 합니다. 기본적으로 최신 버전만 설치 됩니다.

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

### -Command

검색 하는 명령을 하나 이상 지정 합니다 `Install-Package` .

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Smi-s

구성 파일을 포함 하는 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -포함

`Install-Package`**Contains** 매개 변수가 개체의 속성 값과 일치 하는 값을 지정 하는 경우 개체를 가져옵니다.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다. **User01** , **Domain01\User01** 등의 사용자 이름을 입력 하거나, cmdlet에 의해 생성 되는 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

**Credential** 매개 변수를 지정 하지 않으면는 `Install-Package` 현재 사용자를 사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Destination

입력 개체의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Get-dscresource

에서 검색 한 하나 이상의 DSC (Desired State Configuration) 리소스를 지정 합니다 `Install-Package` . Cmdlet을 사용 `Find-DscResource` 하 여 DSC 리소스를 찾을 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExcludeVersion

스위치를 전환 하 여 폴더 경로에서 버전 번호를 제외 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

**이름** 및 **설명** 속성에서 검색할 조건을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterOnTag

결과를 필터링 하 고 지정 된 태그를 포함 하지 않는 결과를 제외 하는 태그를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다. 는 보안을 제외 하 고 다음이 발생 하지 않도록 하는 제한을 재정의 합니다 `Install-Package` .

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

### -ForceBootstrap

**PackageManagement** 가 지정 된 패키지에 대 한 패키지 공급자를 자동으로 설치 하도록 합니다.

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

### -헤더

패키지 헤더를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -포함

에서 모든 패키지 유형을 찾아야 하는지 여부를 지정 합니다 `Install-Package` . 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- cmdlet
- DscResource
- 함수
- RoleCapability
- 워크플로

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

파이프라인 입력을 허용 합니다. 패키지의 **\Id** 유형을 사용 하 여 패키지를 지정 합니다.
`Find-Package`**\Id** 개체를 출력 합니다.

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -InstallUpdate

에서 업데이트를 설치 함을 나타냅니다 `Install-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

설치 하려는 최대 허용 패키지 버전을 지정 합니다. 이 매개 변수를 지정 하지 않으면에서 `Install-Package` 패키지의 최신 버전을 설치 합니다.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

설치 하려는 최소 허용 패키지 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면 `Install-Package` 은 **MaximumVersion** 매개 변수로 지정 된 모든 버전을 충족 하는 패키지의 최신 버전을 설치 합니다.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

하나 이상의 패키지 이름을 지정 합니다. 여러 패키지 이름을 쉼표로 구분 해야 합니다.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoPathUpdate

**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` . **Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Install-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

**PackageManagement** 공급자의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

패키지 검색의 범위를 지정할 패키지 공급자 이름을 하나 이상 지정 합니다. `Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PublishLocation

패키지의 게시 된 위치에 대 한 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

설치 하려는 패키지의 정확한 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면 `Install-Package` 은 **MaximumVersion** 매개 변수로 지정 된 모든 버전을 충족 하는 패키지의 최신 버전을 설치 합니다.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Find-rolecapability

역할 기능의 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -범위

패키지를 설치할 범위를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- CurrentUser
- AllUsers

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

스크립트의 게시 된 위치에 대 한 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

스크립트 원본 위치를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

소프트웨어 종속성의 설치를 건너뜁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

설치 된 버전 보다 최신 버전의 패키지 버전을 가져올 수 있습니다. 예를 들어 신뢰할 수 있는 게시자가 디지털 서명 하지만 새 버전은 디지털 서명 되지 않은 설치 된 패키지입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

패키지의 자격 증명에 대 한 유효성 검사를 건너뛰는 스위치입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

패키지 소스를 하나 이상 지정 합니다. 여러 패키지 원본 이름을 쉼표로 구분 해야 합니다.
Cmdlet을 실행 하 여 패키지 원본 이름을 가져올 수 있습니다 `Get-PackageSource` .

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tag

패키지 메타 데이터에서 검색할 문자열을 하나 이상 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

모듈, 스크립트 또는 둘 다를 포함 하는 패키지를 검색할지 여부를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 모듈
- 스크립트
- 모두

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

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

### -WhatIf

Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Install-Package` . cmdlet은 실행되지 않습니다.

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

### `Install-Package` 파이프라인의 입력을 허용 합니다.

## 출력

### \Id []

## 참고

명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다. 동적 매개 변수는 패키지 공급자에만 적용 됩니다. `Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다. 예를 들어,에는, `Install-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Find-DscResource](../PowershellGet/Find-DscResource.md)

[Get-Help](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-Package](Get-Package.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Find-Package](Find-Package.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)
