---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: ceae77cb6ef2e36f62da7872e9592292e6065ada
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214825"
---
# Install-PackageProvider

## 개요
하나 이상의 패키지 관리 패키지 공급자를 설치 합니다.

## SYNTAX

### PackageBySearch (기본값)

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### PackageByInputObject

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

**Install-packageprovider** Cmdlet은 **PowerShellGet** 에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.
기본적으로 여기에는 **PackageManagement** 태그를 사용 하 여 PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다.
**PowerShellGet** 패키지 관리 공급자는 이러한 리포지토리에서 공급자를 찾는 데 사용 됩니다.

또한이 cmdlet은 패키지 관리 부트스트래핑 응용 프로그램을 통해 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.

또한이 cmdlet은 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.
부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.

처음 실행 하려면 PackageManagement에서 Nuget 패키지 공급자를 다운로드 하려면 인터넷에 연결 되어 있어야 합니다.
그러나 컴퓨터에 인터넷 연결이 없고 Nuget 또는 PowerShellGet 공급자를 사용 해야 하는 경우에는 다른 컴퓨터에서 다운로드 하 여 대상 컴퓨터에 복사할 수 있습니다.
이렇게 하려면 다음 절차를 따릅니다.

1.
`Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force`을 실행 하 여 인터넷에 연결 된 컴퓨터에서 공급자를 설치 합니다.

2.
설치 후 또는에 설치 된 공급자를 찾을 수 있습니다 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .

3.
\<ProviderName\>폴더 (이 경우에는 Nuget 폴더)를 대상 컴퓨터의 해당 위치에 배치 합니다.
대상 컴퓨터가 Nano 서버인 경우 Nano Server에서 **install-packageprovider** 를 실행 하 여 올바른 Nuget 이진 파일을 다운로드 해야 합니다.

4.
PowerShell을 다시 시작 하 여 패키지 공급자를 자동으로 로드 합니다.
또는를 실행 `Get-PackageProvider -ListAvailable` 하 여 컴퓨터에서 사용할 수 있는 패키지 공급자를 모두 나열 합니다.
그런 다음 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 를 사용 하 여 공급자를 현재 PowerShell 세션으로 가져옵니다.

## 예제

### 예제 1: PowerShell 갤러리에서 패키지 공급자 설치

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

이 명령은 PowerShell 갤러리에서 Gistprovider를 설치 합니다.

### 예 2: 지정 된 버전의 패키지 공급자 설치

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

이 예제에서는 지정 된 버전의 Nuget 패키지 공급자를 설치 합니다.

첫 번째 명령은 Nuget 이라는 패키지 공급자의 모든 버전을 찾습니다.
두 번째 명령은 지정 된 버전의 Nuget 패키지 공급자를 설치 합니다.

### 예 3: 공급자 찾기 및 설치

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

이 명령은 **install-packageprovider** 및 파이프라인을 사용 하 여 요점 공급자를 검색 하 고 설치 합니다.

### 예제 4: 현재 사용자의 모듈 폴더에 공급자 설치

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

이 명령은 $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies에 패키지 공급자를 설치 하 여 현재 사용자만 사용할 수 있도록 합니다.

## PARAMETERS

### -Allversions)

이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 설치 함을 나타냅니다.
기본적으로 **install-packageprovider** 는 사용 가능한 가장 높은 버전만 반환 합니다.

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

### -Credential

패키지 공급자를 설치할 수 있는 권한을 가진 사용자 계정을 지정 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 모든 작업을 수행 하도록 지정 합니다.
현재는 *Force* 매개 변수가 *forcebootstrap* 매개 변수와 동일 하 게 작동 한다는 것을 의미 합니다.

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

이 cmdlet이 패키지 공급자를 자동으로 설치 함을 나타냅니다.

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

**\Identity** 개체를 지정 합니다.
**Install-packageprovider** cmdlet을 사용 하 여 **install-packageprovider** 에 파이프 하기 위한 **\id** 개체를 가져옵니다.

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

### -MaximumVersion

설치 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다.
이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.

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

설치 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다.
이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 요구 사항을 충족 하는 사용 가능한 가장 높은 버전의 패키지를 설치 합니다.

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

패키지 공급자 모듈 이름을 하나 이상 지정 합니다.
여러 패키지 이름을 쉼표로 구분 합니다.
와일드카드 문자는 지원되지 않습니다.

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

### -프록시

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

### -RequiredVersion

설치 하려는 패키지 공급자의 정확한 허용 버전을 지정 합니다.
이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.

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

공급자의 설치 범위를 지정 합니다.
이 매개 변수에 허용 되는 값은 **AllUsers** 및 **CurrentUser** 입니다.

**AllUsers** 범위는 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 공급자를 설치 합니다.
기본적으로 **$env:P rogramfiles\packagemanagement\providerassemblies.** 입니다.

**CurrentUser** 범위는 현재 사용자만 액세스할 수 있는 위치에 공급자를 설치 합니다.
기본적으로 **$env입니다. LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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

### -Source

패키지 소스를 하나 이상 지정 합니다.
Get-PackageSource cmdlet을 사용 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.

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

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

### Microsoft PackageManagement. 패키지 Id

이 cmdlet에는 개체 **id** 개체를 파이프 하 여 지정할 수 있습니다.
Find-PackageProvider를 사용 하 여 **install-packageprovider** 로 파이프 될 수 있는 **\id** 개체를 가져옵니다.

## 출력

## 참고

## 관련 링크

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)
