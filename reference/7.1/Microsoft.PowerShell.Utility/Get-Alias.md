---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: e0a08a4ee6f00702f765bc359a20bf9e30b9b1c5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213106"
---
# Get-Alias

## 개요
현재 세션의 별칭을 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### 정의

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## 설명

이 **cmdlet은** 현재 세션의 별칭을 가져옵니다.
여기에는 기본 제공 별칭, 사용자가 설정 하거나 가져온 별칭 및 PowerShell 프로필에 추가한 별칭이 포함 됩니다.

기본적 **으로, alias는 별칭을 사용** 하 여 명령 이름을 반환 합니다.
*Definition* 매개 변수를 사용 하는 경우에는 **Get 별칭** 에서 명령 이름을 사용 하 여 해당 별칭을 반환 합니다.

Windows PowerShell 3.0부터 **가져오기 별칭** 에는 하이픈을 사용 하지 않는 별칭 이름이 형식으로 표시 `<alias> -> <definition>` 되므로 필요한 정보를 더 쉽게 찾을 수 있습니다.

## 예제

### 예 1: 현재 세션의 모든 별칭 가져오기

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

이 명령은 현재 세션의 모든 별칭을 가져옵니다.

출력은 `<alias> -> <definition>` Windows PowerShell 3.0에 도입 된 형식을 보여 줍니다.
일반적으로 cmdlet 및 함수 이름에는 애칭 대신 하이픈 있는 별칭을 사용하는 것이 좋으므로 이 형식은 하이픈을 포함하지 않는 별칭에만 사용됩니다.

### 예제 2: 이름으로 별칭 가져오기

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

이 명령은 ps로 끝나는 별칭을 제외 하 고 gp 또는 sp로 시작 하는 모든 별칭을 가져옵니다.

### 예 3: cmdlet에 대 한 별칭 가져오기

```powershell
Get-Alias -Definition Get-ChildItem
```

이 명령은 Get-ChildItem cmdlet의 별칭을 가져옵니다.

기본적으로, 별칭을 알고 있는 경우 **에는 별칭 cmdlet이** 항목 이름을 가져옵니다.
*정의* 매개 변수는 항목 이름을 알고 있을 때 별칭을 가져옵니다.

### 예제 4: 속성으로 별칭 가져오기

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

이 명령은 Options 속성 값이 ReadOnly 인 모든 별칭을 가져옵니다.
이 명령은 읽기 전용 옵션이 있으므로 PowerShell에 기본 제공 되는 별칭을 신속 하 게 찾는 방법을 제공 합니다.

옵션은 System.management.automation.aliasinfo가 **가져오는** 개체의 속성 중 하나일 뿐입니다.
System.management.automation.aliasinfo 개체의 속성 및 메서드를 모두 찾으려면를 입력 `Get-Alias | get-member` 합니다.

### 예 5: 이름을 기준으로 별칭 가져오기 및 시작 문자를 기준으로 필터링

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

이 예제에서는 이름이 "e"로 시작하지 않고 "-PSSession"으로 끝나는 명령의 별칭을 가져옵니다.

이 명령은 *scope* 매개 변수를 사용 하 여 전역 범위에 명령을 적용 합니다.
이 명령은 스크립트에서 세션의 별칭을 가져오려는 경우에 유용합니다.

## PARAMETERS

### -Definition

지정한 항목의 별칭을 가져옵니다.
cmdlet, 함수, 스크립트, 파일 또는 실행 파일의 이름을 입력합니다.

이 매개 변수는 별칭 개체의 Definition 속성에서 항목 이름을 검색 하므로 *정의* 라고 합니다.

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -제외

지정된 항목을 생략합니다.
이 매개 변수 값은 Name 및 Definition 매개 변수를 한정합니다.
이름, 정의 또는 패턴(예: "s*")을 입력합니다.
와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

이 cmdlet이 가져오는 별칭을 지정 합니다.
와일드카드가 지원됩니다.
기본적으로는 `Get-Alias` 현재 세션에 대해 정의 된 모든 별칭을 검색 합니다.
매개 변수 이름 **이름은** 선택 사항입니다.
별칭 이름을로 파이프 할 수도 있습니다 `Get-Alias` .

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -범위

이 cmdlet이 별칭을 가져오는 범위를 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)

Local이 기본값입니다.
자세한 내용은 about_Scopes를 참조하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

**별칭에 별칭** 이름을 지정할 수 있습니다.

## 출력

### System.management.automation.aliasinfo.

**Get-help** 는 각 별칭을 나타내는 개체를 반환 합니다.
**Alias는** 모든 별칭에 대해 동일한 개체를 반환 하지만 PowerShell은 화살표 기반 형식을 사용 하 여 하이픈을 사용 하지 않는 별칭의 이름을 표시 합니다.

## 참고

- 새 별칭을 만들려면 Set-Alias 또는 New-Alias를 사용합니다. 별칭을 삭제하려면 Remove-Item을 사용합니다.
- 하이픈을 포함하는 별칭에는 화살표 기반 별칭 이름 형식이 사용되지 않습니다. 대체로 cmdlet 및 함수의 대체 이름으로 일반적인 약어나 애칭 대신 별칭을 사용하는 것이 좋습니다.

## 관련 링크

[Export-Alias](Export-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[별칭 공급자](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

