---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 8ab8a0fd505bca7cda5cef17a09baa9f7e571dd4
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892800"
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

이 `Install-PackageProvider` cmdlet은 **PowerShellGet** 에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다. 기본적으로이 창에는 **PackageManagement** 태그를 사용 하 여 Windows PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다. **PowerShellGet** 패키지 관리 공급자는 이러한 리포지토리에서 공급자를 찾는 데 사용 됩니다.

또한이 cmdlet은 패키지 관리 부트스트래핑 응용 프로그램을 통해 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.

또한이 cmdlet은 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다. 부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.

처음 실행 하려면 PackageManagement에서 NuGet 패키지 공급자를 다운로드 하려면 인터넷에 연결 되어 있어야 합니다. 그러나 컴퓨터에 인터넷 연결이 없고 NuGet 또는 PowerShellGet 공급자를 사용 해야 하는 경우에는 다른 컴퓨터에서 다운로드 하 여 대상 컴퓨터에 복사할 수 있습니다. 이렇게 하려면 다음 절차를 따릅니다.

1. `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force`을 실행 하 여 인터넷에 연결 된 컴퓨터에서 공급자를 설치 합니다.
1. 설치 후 또는에 설치 된 공급자를 찾을 수 있습니다 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .
1. `<ProviderName>`폴더 (이 경우에는 NuGet 폴더)를 대상 컴퓨터의 해당 위치에 배치 합니다. 대상 컴퓨터가 Nano 서버인 경우 Nano Server에서를 실행 하 여 `Install-PackageProvider` 올바른 NuGet 이진 파일을 다운로드 해야 합니다.
1. PowerShell을 다시 시작 하 여 패키지 공급자를 자동으로 로드 합니다. 또는를 실행 `Get-PackageProvider -ListAvailable` 하 여 컴퓨터에서 사용할 수 있는 패키지 공급자를 모두 나열 합니다.
   그런 다음 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 를 사용 하 여 현재 Windows PowerShell 세션으로 공급자를 가져옵니다.

## 예제

### 예제 1: PowerShell 갤러리에서 패키지 공급자 설치

이 명령은 PowerShell 갤러리에서 GistProvider 패키지 공급자를 설치 합니다.

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### 예 2: 지정 된 버전의 패키지 공급자 설치

이 예제에서는 지정 된 버전의 NuGet 패키지 공급자를 설치 합니다.

첫 번째 명령은 NuGet 이라는 패키지 공급자의 모든 버전을 찾습니다.
두 번째 명령은 지정 된 버전의 NuGet 패키지 공급자를 설치 합니다.

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### 예 3: 공급자 찾기 및 설치

이 예제에서는 및 파이프라인을 사용 하 여 `Find-PackageProvider` 요점 공급자를 검색 하 고 설치 합니다.

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### 예제 4: 현재 사용자의 모듈 폴더에 공급자 설치

이 명령은 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` 현재 사용자만 사용할 수 있도록에 패키지 공급자를 설치 합니다.

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## PARAMETERS

### -Allversions)

이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 설치 함을 나타냅니다. 기본적으로는 `Install-PackageProvider` 사용 가능한 가장 높은 버전만 반환 합니다.

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

이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 모든 작업을 수행 하도록 지정 합니다. 현재는 **Force** 매개 변수가 **forcebootstrap** 매개 변수와 동일 하 게 작동 한다는 것을 의미 합니다.

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

**\Identity** 개체를 지정 합니다. Cmdlet을 사용 하 여를 `Find-PackageProvider` 파이프 하는 개체 **를** 가져옵니다 `Install-PackageProvider` .

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

설치 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면에서 `Install-PackageProvider` 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.

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

설치 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면에서 `Install-PackageProvider` *MaximumVersion* 매개 변수로 지정 된 요구 사항에 부합 하는 사용 가능한 가장 높은 버전의 패키지를 설치 합니다.

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

패키지 공급자 모듈 이름을 하나 이상 지정 합니다. 여러 패키지 이름을 쉼표로 구분 합니다.
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

**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.

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

설치 하려는 패키지 공급자의 정확한 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면에서 `Install-PackageProvider` **MaximumVersion** 매개 변수로 지정 된 최대 버전을 만족 하는 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.

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

공급자의 설치 범위를 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- **AllUsers** -컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 공급자를 설치 합니다.
  기본적으로 **$env:P rogramfiles\packagemanagement\providerassemblies.** 입니다.

- **CurrentUser** -현재 사용자만 액세스할 수 있는 위치에 공급자를 설치 합니다. 기본적으로 **$env입니다. LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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

패키지 소스를 하나 이상 지정 합니다. Cmdlet을 사용 `Get-PackageSource` 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.

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

### Microsoft PackageManagement. 패키지 Id

이 cmdlet에는 개체 **id** 개체를 파이프 하 여 지정할 수 있습니다. 를 사용 `Find-PackageProvider` 하 여로 파이프 될 수 있는 고 지 **id** 개체를 가져옵니다 `Install-PackageProvider` .

## 출력

## 참고

> [!IMPORTANT]
> 2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다. TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다. 다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.

## 관련 링크

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)
