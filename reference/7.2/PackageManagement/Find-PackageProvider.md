---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: cca73714cebf8f0d527c669358458f8509b80a90
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603071"
---
# Find-PackageProvider

## 개요
설치에 사용할 수 있는 패키지 관리 패키지 공급자 목록을 반환 합니다.

## SYNTAX

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## 설명

**Install-packageprovider** Cmdlet은 PowerShellGet에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 PackageManagement 공급자를 찾습니다.
이러한 패키지 공급자는 Install-PackageProvider cmdlet을 사용하여 설치에 사용할 수 있습니다.
기본적으로 여기에는 **PackageManagement** 및 **공급자** 태그를 사용 하 여 PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다.

또한 **install-packageprovider** 는 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 찾습니다.
부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.

## 예제

### 예제 1: 사용 가능한 모든 패키지 공급자 찾기

```
PS C:\> Find-PackageProvider
```

이 명령은 패키지 관리에서 지 원하는 리포지토리에서 사용할 수 있는 모든 패키지 공급자 목록을 가져옵니다.
이러한 패키지 공급자는 기본적으로 PowerShell 갤러리 및 패키지 관리 부트스트래핑 응용 프로그램을 사용 하 여 사용할 수 있습니다.

### 예제 2: 공급자의 모든 버전 찾기

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

이 명령은 Nuget 이라는 패키지 공급자의 모든 버전을 찾습니다.

### 예제 3: 지정 된 소스에서 공급자 찾기

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

이 명령은 지정 된 패키지 원본을 사용 하 여 사용할 수 있는 패키지 공급자를 찾습니다.

## PARAMETERS

### -Allversions)

이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 반환 함을 나타냅니다.
기본적으로 **install-packageprovider** 는 사용 가능한 최신 버전만 반환 합니다.

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

패키지 공급자를 검색할 수 있는 권한이 있는 사용자 계정을 지정 합니다.

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

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.
현재는 *Forcebootstrap* 매개 변수와 같습니다.

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

이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.

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

### -IncludeDependencies

이 cmdlet에 종속성이 포함 되어 있음을 나타냅니다.

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

### -MaximumVersion

검색 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다.
이 매개 변수를 추가 하지 않으면 **install-packageprovider** 에서 사용 가능한 가장 높은 버전의 공급자를 찾습니다.

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

검색 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다.
이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 지정 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.

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

하나 이상의 패키지 공급자 모듈 이름 또는 와일드 카드 문자를 포함 하는 공급자 이름을 지정 합니다.
여러 패키지 이름을 쉼표로 구분 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

찾으려는 패키지 공급자의 정확한 허용 버전을 지정 합니다.
이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 찾습니다.

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

### -Source

패키지 소스를 하나 이상 지정 합니다.
Get-PackageSource cmdlet을 사용 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### Microsoft PackageManagement. 패키지 Id

이 cmdlet은 **\Id** 개체를 반환 합니다.
**Install-packageprovider** 의 결과를 설치 하기 위해 **\Id** 개체를 **install-packageprovider** 에 파이프 하 여 설치할 수 있습니다.

## 참고

> [!IMPORTANT]
> 2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다. TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다. 다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Install-PackageProvider](Install-PackageProvider.md)
