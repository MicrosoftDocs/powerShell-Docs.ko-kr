---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 4be80765181e045f24b1f90243de21f38533bfba
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214809"
---
# Uninstall-Package

## 개요
하나 이상의 소프트웨어 패키지를 제거 합니다.

## SYNTAX

### PackageByInputObject

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PackageBySearch

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### NuGet: PackageByInputObject

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### NuGet: PackageBySearch

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet: PackageByInputObject

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### PowerShellGet: PackageBySearch

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## 설명

`Uninstall-Package`Cmdlet은 로컬 컴퓨터에서 하나 이상의 소프트웨어 패키지를 제거 합니다. 설치 된 패키지를 찾으려면 cmdlet을 사용 `Get-Package` 합니다.

## 예제

### 예제 1: 패키지 제거

`Uninstall-Package`Cmdlet은 패키지를 제거 합니다. **Name** 매개 변수는 제거할 패키지를 지정 합니다. 패키지의 여러 버전을 설치 하는 경우 최신 버전이 제거 됩니다.

```
PS> Uninstall-Package -Name NuGet.Core
```

### 예제 2: 파이프라인을 사용 하 여 패키지 제거

`Get-Package` 특정 패키지를 찾아서 파이프라인에서 cmdlet에 대 한 개체 **id** 개체를 보냅니다 `Uninsall-Package` .

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

`Get-Package`Cmdlet은 **Name** 및 **RequiredVersion** 매개 변수를 사용 하 여 패키지를 지정 합니다.
**\Id** 개체는 파이프라인으로 전송 됩니다. `Uninstall-Package`Cmdlet은 개체를 **InputObject** 로 수신 하 고 패키지를 제거 합니다.

또는 `Uninstall-Package` cmdlet에서 **InputObject** 매개 변수에 대 한 값을 지정할 수 있습니다.

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## PARAMETERS

### -AllowClobber

기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다. 설치 중인 명령과 이름이 같은 기존 명령을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

시험판으로 표시 된 패키지를 제거할 수 있도록 허용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Allversions)

이 cmdlet은 패키지의 모든 버전을 제거 함을 나타냅니다.

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

### -Destination

입력 개체의 경로 문자열을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
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
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -InputObject

Cmdlet에서 패키지의 **\Id** 개체를 지정 하는 파이프라인 입력을 허용 `Get-Package` 합니다. **InputObject** 는 개체를 포함 하는 변수 또는 값으로 **\id** 개체를 수락 합니다 `Get-Package` .

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

에서 업데이트를 제거 함을 나타냅니다 `Uninstall-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

제거 하려는 최대 허용 패키지 버전을 지정 합니다. 이 매개 변수를 지정 하지 않으면에서 `Uninstall-Package` 패키지의 최신 버전을 제거 합니다.

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

제거 하려는 최소 허용 패키지 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면 `Uninstall-Package` 은 **MaximumVersion** 매개 변수로 지정 된 버전을 충족 하는 최신 버전의 패키지를 제거 합니다.

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

**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` . **Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Uninstall-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

**PackageManagement** 공급자를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

패키지를 검색할 패키지 공급자 이름을 하나 이상 지정 합니다. `Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.

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

### -RequiredVersion

제거 하려는 패키지의 정확한 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면 `Uninstall-Package` 은 **MaximumVersion** 매개 변수로 지정 된 버전을 충족 하는 최신 버전의 패키지를 제거 합니다.

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

### -범위

패키지를 제거할 범위를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- CurrentUser
- AllUsers

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

소프트웨어 종속성 제거를 건너뜁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
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
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
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
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
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

Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Uninstall-Package` . Cmdlet이 실행 되지 않습니다.

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

### `Uninstall-Package` 파이프라인의 **\Id** 개체를 입력으로 받아들입니다.

## 출력

### `Uninstall-Package` 는 출력을 생성 하지 않습니다.

## 참고

명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다. 동적 매개 변수는 패키지 공급자에만 적용 됩니다. `Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다. 예를 들어,에는, `Uninstall-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Find-Package](Find-Package.md)

[Get-Package](Get-Package.md)

[Install-Package](Install-Package.md)

[Save-Package](Save-Package.md)
