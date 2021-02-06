---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 20820d2d194f41d43048c9617b63b9acb3fbb4f8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600145"
---
# Get-PSProvider

## 개요
지정 된 PowerShell 공급자에 대 한 정보를 가져옵니다.

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## 설명

`Get-PSProvider`Cmdlet은 현재 세션의 PowerShell 공급자를 가져옵니다.
특정 드라이브를 가져오거나 세션의 모든 드라이브를 가져올 수 있습니다.

PowerShell 공급자를 사용 하면 파일 시스템 드라이브 처럼 다양 한 데이터 저장소에 액세스할 수 있습니다.
PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조 하세요.

## 예제

### 예제 1: 사용 가능한 모든 공급자 목록 표시

```powershell
Get-PSProvider
```

이 명령은 사용 가능한 모든 PowerShell 공급자 목록을 표시 합니다.

### 예 2: 지정 된 문자로 시작 하는 모든 PowerShell 공급자 목록 표시

```powershell
Get-PSProvider f*, r* | Format-List
```

이 명령은 이름이 f 또는 r 문자로 시작 하는 모든 PowerShell 공급자 목록을 표시 합니다.

### 예제 3: 세션에 공급자를 추가한 스냅인 또는 모듈 찾기

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

이러한 명령은 세션에 공급자를 추가한 PowerShell 스냅인 또는 모듈을 찾습니다.
공급자를 비롯 한 모든 PowerShell 요소는 스냅인 이나 모듈에서 시작 됩니다.

이러한 명령은를 반환 하는 **ProviderInfo** 개체의 Add-pssnapin 및 Module 속성을 사용 `Get-PSProvider` 합니다.
이러한 속성 값에는 공급자를 추가하는 스냅인이나 모듈의 이름이 포함됩니다.

첫 번째 명령은 세션의 모든 공급자를 가져와서 해당 Name, Module 및 PSSnapin 속성 값과 함께 테이블 형식으로 표시합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Where-Object` **Microsoft. PowerShell. 보안** 스냅인에서 제공 하는 공급자를 가져옵니다.

### 예 4: 파일 시스템 공급자의 Home 속성 경로 확인

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

이 예에서는 물결표 기호 (~)가 FileSystem 공급자의 **Home** 속성 값을 나타내는 것을 보여 줍니다.
**Home** 속성 값은 선택 사항 이지만 **FileSystem** 공급자의 경우 또는로 정의 됩니다 `$env:homedrive\$env:homepath` `$home` .

## PARAMETERS

### -PSProvider

이 cmdlet이 정보를 가져오는 PowerShell 공급자의 이름 또는 이름을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### String[]

하나 이상의 공급자 이름 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### ProviderInfo.

이 cmdlet은 세션의 PowerShell 공급자를 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

