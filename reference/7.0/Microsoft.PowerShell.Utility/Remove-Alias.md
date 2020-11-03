---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 6f98a910e43b87793ac4f2af8ffb069d3e5d47ba
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210289"
---
# Remove-Alias

## 개요
현재 세션에서 별칭을 제거 합니다.

## SYNTAX

### Default (기본값)

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## 설명

`Remove-Alias`Cmdlet은 현재 PowerShell 세션에서 별칭을 제거 합니다. **Option** 속성이 **ReadOnly** 로 설정 된 별칭을 제거 하려면 **Force** 매개 변수를 사용 합니다.

`Remove-Alias`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.

## 예제

### 예제 1-별칭 제거

이 예에서는 cmdlet을 나타내는 라는 별칭을 제거 합니다 `del` `Remove-Item` .

```powershell
Remove-Alias -Name del
```

### 예제 2-비상수 별칭 모두 제거

이 예에서는 **Options** 속성이 **상수로** 설정 된 별칭을 제외 하 고 현재 PowerShell 세션에서 모든 별칭을 제거 합니다. 명령을 실행 한 후에는 다른 PowerShell 세션 또는 새로운 PowerShell 세션에서 별칭을 사용할 수 있습니다.

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

`Get-Alias` PowerShell 세션의 모든 별칭을 가져오고 개체를 파이프라인으로 보냅니다.
`Where-Object` 는 스크립트 블록을 사용 하 고 자동 변수 ( `$_` ) 및 **옵션** 속성은 현재 파이프라인 개체를 나타냅니다. **NE** (같지 않음) 매개 변수는 **옵션** 값이 **상수로** 설정 되지 않은 개체를 선택 합니다. `Remove-Alias`**Force** 매개 변수를 사용 하 여 PowerShell 세션에서 읽기 전용 별칭을 포함 하 여 별칭을 제거 합니다.

## PARAMETERS

### -Force

**옵션** 속성이 **ReadOnly** 로 설정 된 별칭을 포함 하 여 cmdlet이 별칭을 제거 함을 나타냅니다. **Force** 매개 변수는 **옵션** 속성이 **상수로** 설정 된 별칭을 제거할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

제거할 별칭의 이름을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -범위

지정 된 범위에 있는 별칭에만 영향을 줍니다. 기본 범위는 **Local** 입니다. 자세한 내용은 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)를 참조 하세요.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)

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

### System.String[]

별칭 개체를 파이프로 파이프 하 여 **제거할** 수 있습니다.

## 출력

### 없음

이 cmdlet은 출력을 반환 하지 않습니다.

## 참고

변경 내용은 현재 범위에만 영향을 줍니다. 모든 세션에서 별칭을 제거 하려면 PowerShell 프로필에 **제거 별칭** 명령을 추가 합니다.

자세한 내용은 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)를 참조 하세요.

## 관련 링크

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
