---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215401"
---
# Get-PSProvider

## 개요
지정된 Windows PowerShell 공급자에 대한 정보를 가져옵니다.

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## 설명
**Get PSProvider** cmdlet은 현재 세션의 Windows PowerShell 공급자를 가져옵니다.
특정 드라이브를 가져오거나 세션의 모든 드라이브를 가져올 수 있습니다.

Windows PowerShell 공급자는 다양한 데이터 원본이 파일 시스템 드라이브에 있을 때처럼 데이터 원본에 액세스할 수 있도록 지원합니다.
Windows PowerShell 공급자에 대한 자세한 내용은 about_Providers를 참조하세요.

## 예제

### 예제 1: 사용 가능한 모든 공급자 목록 표시

```
PS C:\> Get-PSProvider
```

이 명령은 사용 가능한 모든 Windows PowerShell 공급자 목록을 표시합니다.

### 예 2: 지정 된 문자로 시작 하는 모든 Windows PowerShell 공급자 목록을 표시 합니다.

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

이 명령은 이름이 f 또는 r 문자로 시작 하는 모든 Windows PowerShell 공급자 목록을 표시 합니다.

### 예제 3: 세션에 공급자를 추가한 스냅인 또는 모듈 찾기

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

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

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

이들 명령은 사용자 세션에 공급자를 추가한 Windows PowerShell 스냅인 또는 모듈을 찾습니다.
공급자를 포함하여 모든 Windows PowerShell 요소는 스냅인이나 모듈에서 제공합니다.

이러한 명령은 **Get PSProvider** 가 반환 하는 **ProviderInfo** 개체의 add-pssnapin 및 Module 속성을 사용 합니다.
이러한 속성 값에는 공급자를 추가하는 스냅인이나 모듈의 이름이 포함됩니다.

첫 번째 명령은 세션의 모든 공급자를 가져와서 해당 Name, Module 및 PSSnapin 속성 값과 함께 테이블 형식으로 표시합니다.

두 번째 명령은 Where-Object cmdlet을 사용 하 여 **Microsoft. PowerShell. 보안** 스냅인에서 제공 하는 공급자를 가져옵니다.

### 예 4: 파일 시스템 공급자의 Home 속성 경로 확인

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

이 예제에서는 물결표 기호(~)가 FileSystem 공급자의 Home 속성 값을 나타냄을 보여 줍니다.
Home 속성 값은 선택 사항 이지만 FileSystem 공급자의 경우 $env: homedrive \$ env: homepath 또는 $home으로 정의 됩니다.

## PARAMETERS

### -PSProvider
이 cmdlet이 정보를 가져오는 Windows PowerShell 공급자의 이름 또는 이름을 지정 합니다.

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
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### String[]

하나 이상의 공급자 이름 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### ProviderInfo.
이 cmdlet은 세션의 Windows PowerShell 공급자를 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

## 관련 링크
