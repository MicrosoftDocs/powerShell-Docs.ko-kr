---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 00ef887dc79e35a6dff299a37bfafa57aebc77db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213825"
---
# New-Alias

## 개요
새 별칭을 만듭니다.

## SYNTAX

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**새 별칭** cmdlet은 현재 Windows PowerShell 세션에 새 별칭을 만듭니다.
세션을 종료 하거나 Windows PowerShell을 닫은 후에는 **새 별칭** 을 사용 하 여 만든 별칭이 저장 되지 않습니다.
Export-Alias cmdlet을 사용하여 파일에 별칭 정보를 저장할 수 있습니다.
나중에 **Import-alias** 를 사용 하 여 저장 된 별칭 정보를 검색할 수 있습니다.

## 예제

### 예제 1: cmdlet에 대 한 별칭 만들기

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

이 명령은 Get-ChildItem cmdlet을 나타내는 별칭 이라는 이름의 별칭을 만듭니다.

### 예제 2: cmdlet에 대 한 읽기 전용 별칭 만들기

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

이 명령은 Get-WmiObject cmdlet을 나타내는 W 라는 별칭을 만듭니다.
별칭에 대 한 설명, 빠른 wmi 별칭을 만들고 읽기 전용으로 만듭니다.
명령의 마지막 줄은 Get-Alias를 사용하여 새 별칭을 가져오고 이를 Format-List로 파이프하여 그에 대한 모든 정보를 표시합니다.

## PARAMETERS

### -Description
별칭에 대한 설명을 지정합니다.
아무 문자열이나 입력할 수 있습니다.
설명에 공백이 포함되어 있으면 따옴표로 묶습니다.

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

### -Force
이라는 별칭이 이미 있는 경우 cmdlet이 Set-Alias 처럼 동작 함을 나타냅니다.

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
새 별칭을 지정합니다.
별칭에는 모든 영숫자 문자를 사용할 수 있지만 첫 문자는 숫자가 아니어야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -옵션
별칭의 **Options** 속성 값을 지정 합니다.
유효한 값은 다음과 같습니다.

- 없음: 별칭에 제약 조건 (기본값)이 없습니다.
- ReadOnly: 별칭을 삭제할 수는 있지만 **Force** 매개 변수를 사용 하는 경우를 제외 하 고는 변경할 수 없습니다.
- 상수: 별칭을 삭제 하거나 변경할 수 없습니다.
- 비공개: 별칭은 현재 범위 에서만 사용할 수 있습니다.
- AllScope: 별칭이 만들어진 모든 새 범위에 복사 됩니다.
- 지정 되지 않음: 옵션이 지정 되지 않았습니다.

세션에 있는 모든 별칭의 **Options** 속성을 보려면를 입력 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 합니다.

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
작업 중인 항목을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -범위
새 별칭의 범위를 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.

Local이 기본값입니다.
자세한 내용은 about_Scopes를 참조하세요.

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

### -Value
별칭을 지정할 cmdlet 또는 명령 요소의 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
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

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음 또는 System.management.automation.aliasinfo
*Passthru* 매개 변수를 사용 하는 경우 **새** 별칭을 나타내는 **system.management.automation.aliasinfo** 개체가 생성 됩니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 새 별칭을 만들려면 Set-Alias 또는 New-Alias를 사용합니다. 별칭을 변경 하려면 **Set-alias** 를 사용 합니다. 별칭을 삭제하려면 Remove-Item을 사용합니다.

*

## 관련 링크

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[Set-Alias](Set-Alias.md)
