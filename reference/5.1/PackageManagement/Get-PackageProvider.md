---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: 03bb3f427f86867fdfe392b7b153c14b333e0fe3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213298"
---
# Get-PackageProvider

## 개요
패키지 관리에 연결 된 패키지 공급자의 목록을 반환 합니다.

## SYNTAX

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## 설명
**Install-packageprovider** cmdlet은 패키지 관리에 연결 된 패키지 공급자 목록을 반환 합니다.
이러한 공급자의 예로는 PSModule, NuGet 및 Chocolatey이 있습니다.
하나 이상의 공급자 이름 전체 또는 일부를 기준으로 결과를 필터링 할 수 있습니다.

## 예제

### 예제 1: 현재 로드 된 패키지 공급자 모두 가져오기

```
PS C:\> Get-PackageProvider
```

이 명령은 로컬 컴퓨터에 현재 로드 된 모든 패키지 공급자 목록을 가져옵니다.

### 예제 2: 사용 가능한 패키지 공급자 모두 가져오기

```
PS C:\> Get-PackageProvider -ListAvailable
```

이 명령은 로컬 컴퓨터에서 사용할 수 있는 모든 패키지 공급자 목록을 가져옵니다.

### 예제 3: 동적으로 패키지 공급자 가져오기

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

이 명령은 컴퓨터에 Chocolatey 공급자가 설치 되어 있지 않은 경우 Chocolatey 공급자를 자동으로 설치 합니다.

## PARAMETERS

### -Force
이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 다른 모든 작업을 수행 하도록 지정 합니다.
**Install-packageprovider** 에서 *Force* 매개 변수는 *forcebootstrap* 매개 변수와 동일 하 게 작동 합니다.

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

### -ListAvailable
설치 된 모든 공급자를 가져옵니다.
**Install-packageprovider** 는 **PSModulePath** 환경 변수에 나열 된 경로 및 패키지 공급자 어셈블리 폴더에 대 한 공급자를 가져옵니다.

**$env:P rogramFiles\PackageManagement\ProviderAssemblies * * * * $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**

이 매개 변수를 **사용** 하지 않으면 install-packageprovider는 현재 세션에 로드 된 공급자만 가져옵니다.

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

### -Name
하나 이상의 공급자 이름 또는 일부 공급자 이름을 지정 합니다.
여러 공급자 이름을 쉼표로 구분 합니다.
이 매개 변수에 유효한 값은 패키지와 함께 설치한 공급자의 이름을 포함 합니다. PackageManagement는 **Psmodule** 및 **MSI** 공급자를 비롯 한 기본 공급자 집합과 함께 제공 됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### Install-packageprovider []

## 참고

## 관련 링크

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Unregister-PackageSource](Unregister-PackageSource.md)
