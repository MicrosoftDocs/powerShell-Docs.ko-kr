---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c6604b06f8ff971bc18d9811bd23b6932b9f414c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210466"
---
# Get-Package

## 개요
**PackageManagement** 를 사용 하 여 설치 된 모든 소프트웨어 패키지 목록을 반환 합니다.

## SYNTAX

### NuGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## 설명

`Get-Package`Cmdlet은 **PackageManagement** 를 사용 하 여 설치 된 로컬 컴퓨터의 모든 소프트웨어 패키지 목록을 반환 합니다. `Get-Package`또는 명령이 나 스크립트의 일부로 실행 하 여 원격 컴퓨터에서를 실행할 수 있습니다 `Invoke-Command` `Enter-PSSession` .

## 예제

### 예제 1: 설치 된 모든 패키지 가져오기

`Get-Package`Cmdlet은 로컬 컴퓨터에 설치 된 모든 패키지를 가져옵니다.

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### 예 2: 원격 컴퓨터에 설치 된 패키지 가져오기

이 명령은 원격 컴퓨터에서 **PackageManagement** 에 의해 설치 된 패키지 목록을 가져옵니다. 이 명령은 지정 된 사용자의 암호를 제공 하 라는 메시지를 표시 합니다.

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

`Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터 **Server01** 를 지정 합니다. **Credential** 매개 변수는 컴퓨터에서 명령을 실행할 수 있는 권한이 있는 도메인 및 사용자 이름을 지정 합니다. **ScriptBlock** 매개 변수는 `Get-Package` 원격 컴퓨터에서 cmdlet을 실행 합니다.

### 예제 3: 지정 된 공급자에 대 한 패키지 가져오기

이 명령은 특정 공급자의 로컬 컴퓨터에 설치 된 소프트웨어 패키지를 가져옵니다.

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package`**ProviderName** 매개 변수를 사용 하 여 특정 공급자 **PowerShellGet** 을 지정 합니다.
**모든** 버전 매개 변수는 설치 된 각 버전을 표시 합니다.

### 예제 4: 특정 패키지의 정확한 버전 가져오기

이 명령은 설치 된 패키지의 특정 버전을 가져옵니다. 패키지의 여러 버전을 설치할 수 있습니다.

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package`**name** 매개 변수를 사용 하 여 패키지 이름 **PackageManagement** 를 지정 합니다. **ProviderName** 매개 변수는 공급자 ( **PowerShellGet** )를 지정 합니다. **필수 버전** 매개 변수는 설치 된 버전을 지정 합니다.

### 예 5: 패키지 제거

이 예에서는 패키지 정보를 가져온 다음 패키지를 제거 합니다.

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

`Get-Package`**name** 매개 변수를 사용 하 여 **posh-git** 패키지 이름을 지정 합니다. **RequiredVersion** 매개 변수는 패키지의 특정 버전입니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Uninstall-Package` . `Uninstall-Package` 패키지를 제거 합니다.

## PARAMETERS

### -AllowClobber

기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다. 모듈에 의해 설치 되는 명령과 이름이 같은 기존 명령을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

결과에서 시험판으로 표시 된 패키지를 포함 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Allversions)

에서 `Get-Package` 사용 가능한 패키지 버전을 모두 반환 함을 나타냅니다. 기본적으로는 `Get-Package` 사용 가능한 최신 버전만 반환 합니다.

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

압축을 푼 패키지 파일을 포함 하는 디렉터리의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NuGet
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
Parameter Sets: NuGet
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

PackageManagement에서 `Get-Package` 패키지 **PackageManagement** 공급자를 자동으로 설치 하도록 지정 합니다.

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

### -InstallUpdate

이 cmdlet이 업데이트를 설치 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

검색 하려는 최대 패키지 버전을 지정 합니다.

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

### -MinimumVersion

찾으려는 최소 패키지 버전을 지정 합니다. 더 높은 버전을 사용할 수 있는 경우 해당 버전이 반환 됩니다.

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

### -Name

하나 이상의 패키지 이름 또는 와일드 카드 문자를 포함 하는 패키지 이름을 지정 합니다. 여러 패키지 이름을 쉼표로 구분 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -NoPathUpdate

**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` . **Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Get-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

패키지 관리 공급자의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

패키지 공급자 이름을 하나 이상 지정 합니다. 여러 패키지 공급자 이름을 쉼표로 구분 합니다.
사용 `Get-PackageProvider` 가능한 패키지 공급자 목록을 가져오는 데 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

찾을 패키지의 정확한 버전을 지정 합니다.

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

### -범위

패키지에 대 한 검색 범위를 지정 합니다.

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

### -SkipDependencies

에서 패키지 종속성 찾기를 건너뛰도록 지정 하는 스위치입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
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
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

모듈, 스크립트 또는 중 하나를 사용 하 여 패키지를 검색할지 여부를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### \Id []

## 참고

명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다. 동적 매개 변수는 패키지 공급자에만 적용 됩니다. `Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다. 예를 들어,에는, `Get-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[Find-Package](Find-Package.md)

[Get-Help](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Install-Package](Install-Package.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)
