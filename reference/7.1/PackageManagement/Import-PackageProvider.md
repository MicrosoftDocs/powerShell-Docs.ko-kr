---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 428cb3afa574345ef5cb4b79b76b31cf9bfb2e7b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890082"
---
# Import-PackageProvider

## 개요
현재 세션에 패키지 관리 패키지 공급자를 추가 합니다.

## SYNTAX

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## 설명

`Import-PackageProvider`Cmdlet은 현재 세션에 패키지 공급자를 하나 이상 추가 합니다.
가져오는 공급자를 로컬 컴퓨터에 설치 해야 합니다.

사용 가능한 공급자 목록을 가져오려면를 실행 `Get-PackageProvider -ListAvailable` 합니다.
패키지 공급자 이름은 해당 모듈 이름과 다를 수 있습니다.

보안상의 이유로 **PackageManagement** 에는를 포함 하는 c # 기반 공급자가 필요 `provider.manifest` 합니다. 삽입 된 공급자를 빌드하는 방법에 대 한 자세한 내용은 `provider.manifest` `.csproj` 의 프로젝트 파일을 참조 하십시오 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .

## 예제

### 예 1: 로컬 컴퓨터에서 패키지 공급자 가져오기

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

이 명령은 로컬 컴퓨터에 설치 된 Nuget 공급자를 가져옵니다.

### 예제 2: 패키지 공급자의 특정 버전 가져오기

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

이 명령은 특정 버전의 Nuget 패키지 공급자를 찾아서 설치 하 고 가져옵니다.

## PARAMETERS

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.
패키지 공급자를 다시 가져옵니다.

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

### -MaximumVersion

가져올 패키지 공급자의 최대 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.

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

가져올 패키지 공급자의 최소 허용 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` *MaximumVersion* 매개 변수를 사용 하 여 지정 된 최대 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 가져옵니다.

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

패키지 공급자 이름을 하나 이상 지정 합니다. 와일드카드는 사용할 수 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

가져올 패키지 공급자의 정확한 버전을 지정 합니다. 이 매개 변수를 추가 하지 않으면에서 `Import-PackageProvider` **MaximumVersion** 매개 변수를 사용 하 여 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 가져옵니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Install-packageprovider.

에서 반환 하는 **install-packageprovider** 개체를로 파이프 할 수 있습니다 `Get-PackageProvider` `Import-PackageProvider` .

## 출력

## 참고

> [!IMPORTANT]
> 2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다. TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다. 다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Get-PackageProvider](Get-PackageProvider.md)
