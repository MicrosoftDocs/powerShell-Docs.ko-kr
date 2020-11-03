---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: c6347ea9ca2169c6379871131bc98001bcdb5d25
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218882"
---
# Remove-Variable

## 개요
변수와 그 값을 삭제합니다.

## SYNTAX

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Remove-Variable`Cmdlet은 변수가 정의 된 범위 (예: 현재 세션)에서 변수와 그 값을 삭제 합니다. 이 cmdlet을 사용하여 상수로 설정된 변수나 시스템에서 소유한 변수를 삭제할 수 없습니다.

## 예제

### 예제 1: 변수 제거

```powershell
Remove-Variable Smp
```

이 명령은 변수를 삭제 `$Smp` 합니다.

## PARAMETERS

### -제외

이 cmdlet이 작업에서 생략 하는 항목의 배열을 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴(예: "*s*")을 입력합니다. 와일드카드가 지원됩니다.

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

### -Force

변수가 읽기 전용인 경우에도 cmdlet이 해당 변수를 제거 함을 나타냅니다. **Force** 매개 변수를 사용 해도 cmdlet은 상수를 제거할 수 없습니다.

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

### -포함

작업에서이 cmdlet이 삭제 하는 항목의 배열을 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예: s *)을 입력 합니다. 와일드카드가 지원됩니다.

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

제거할 변수의 이름을 지정합니다. 매개 변수 이름 ( **name** )은 선택 사항입니다.
와일드 카드를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -범위

지정한 범위의 변수만 가져옵니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)

Local이 기본값입니다. 자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

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

### System.object입니다.

변수 개체를로 파이프 할 수 있습니다 `Remove-Variable` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

- 변경 내용은 세션과 같은 현재 범위에만 적용됩니다. 모든 세션에서 변수를 삭제 하려면 `Remove-Variable` PowerShell 프로필에 명령을 추가 합니다.

- 의 기본 제공 별칭인를 참조할 수도 있습니다 `Remove-Variable` `rv` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

## 관련 링크

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Set-Variable](Set-Variable.md)
