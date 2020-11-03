---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 6208e9c1b7124c8faec1e3e87a6e815540d2b962
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211417"
---
# Clear-Variable

## 개요
변수 값을 삭제합니다.

## SYNTAX

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

**Clear 변수** cmdlet은 변수에 저장 된 데이터를 삭제 하지만 변수는 삭제 하지 않습니다.
따라서 변수의 값은 NULL(비어 있음)입니다.
변수에 지정 된 데이터 또는 개체 형식이 있는 경우이 cmdlet은 변수에 저장 된 개체의 형식을 유지 합니다.

## 예제

### 예제 1: 검색 문자열로 시작 하는 전역 변수 값 제거

```
PS C:\> Clear-Variable my* -Scope Global
```

이 명령은 이름이 my로 시작 하는 전역 변수의 값을 제거 합니다.

### 예 2: 자식 범위에서 변수를 지우고 부모 범위는 해제

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

이 명령은 하위 범위의 변수를 삭제해도 상위 범위의 값이 삭제되지 않음을 확인합니다.
첫 번째 명령은 $A 변수의 값을 3으로 설정 합니다.
두 번째 명령은 invoke 연산자 (&)를 사용 하 여 새 범위에서 **Clear Variable** 명령을 실행 합니다.
하위 범위에서는 변수가 지워지지만 로컬 범위에서는 지워지지 않습니다.
$A 값을 가져오는 세 번째 명령은 값 3이 영향을 받지 않았음을 보여 줍니다.

### 예 3: 지정 된 변수의 값을 삭제 합니다.

```
PS C:\> Clear-Variable -Name "Processes"
```

이 명령은 명명 된 프로세스 변수의 값을 삭제 합니다.
Cmdlet이 작업을 완료 한 후에는 명명 된 프로세스 변수가 여전히 존재 하지만 값은 null입니다.

## PARAMETERS

### -제외

이 cmdlet이 작업에서 생략 하는 항목의 배열을 지정 합니다.
이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.
이름 요소 또는 패턴(예: "*s*")을 입력합니다.
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

### -Force

변수가 읽기 전용인 경우에도 cmdlet이 해당 변수를 지울 수 있도록 합니다.
Force 매개 변수를 사용해도 cmdlet은 상수를 지울 수 없습니다.

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

이 cmdlet이 작업에 포함 하는 항목의 배열을 지정 합니다.
이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.
이름 요소 또는 패턴(예: "*s*")을 입력합니다.
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

지울 변수의 이름을 지정합니다.
와일드카드가 지원됩니다.
이 매개 변수는 필수이지만 매개 변수 이름("Name")은 선택 사항입니다.

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

이 별칭이 유효한 범위를 지정합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트

현재 범위 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)를 기준으로 하는 숫자를 사용할 수도 있습니다.
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

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### None 또는 System.object입니다.

*PassThru* 매개 변수를 사용 하는 경우이 cmdlet은 지워진 변수를 나타내는 **system.object** 를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 변수와 변수 값을 함께 삭제하려면 Remove-Variable 또는 Remove-Item을 사용합니다.

  이 cmdlet은 *Force* 매개 변수를 사용 하는 경우에도 상수로 설정 되거나 시스템에서 소유 하는 변수의 값을 삭제 하지 않습니다.

  삭제하려는 변수가 없는 경우 cmdlet의 영향을 받지 않습니다.
값이 Null인 변수는 만들지 않습니다.

  기본 제공 별칭인 clv로 **Clear 변수** 를 참조할 수도 있습니다.
자세한 내용은 about_Aliases를 참조하세요.

*

## 관련 링크

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
