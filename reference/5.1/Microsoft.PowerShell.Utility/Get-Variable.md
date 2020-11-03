---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 9fd99e346d97b9a39298170371164753cf04dad8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213906"
---
# Get-Variable

## 개요
현재 콘솔에 있는 변수를 가져옵니다.

## SYNTAX

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## 설명

`Get-Variable`Cmdlet은 현재 콘솔의 PowerShell 변수를 가져옵니다.
**ValueOnly** 매개 변수를 지정하여 변수 값만 검색할 수 있으며 이름을 기준으로 반환되는 변수를 필터링할 수도 있습니다.

## 예제

### 예제 1: 문자별 변수 가져오기

이 명령은 이름이 m 문자로 시작 하는 변수를 가져옵니다.
변수 값도 가져옵니다.

```powershell
Get-Variable m*
```

### 예제 2: 문자별로 변수 값 가져오기

이 명령은 이름이 m으로 시작 하는 변수의 값만 가져옵니다.

```powershell
Get-Variable m* -ValueOnly
```

### 예 3: 두 문자로 변수 가져오기

이 명령은 문자 M 또는 문자 P로 시작 하는 변수에 대 한 정보를 가져옵니다.

```powershell
Get-Variable -Include M*,P*
```

### 예제 4: 범위로 변수 가져오기

첫 번째 명령은 로컬 범위에 정의되어 있는 변수만 가져옵니다.
와 같으며로 `Get-Variable -Scope Local` 약식 일 수 있습니다 `gv -s 0` .

두 번째 명령은 cmdlet을 사용 하 여 `Compare-Object` 부모 범위 (범위 1)에 정의 되어 있지만 로컬 범위 (범위 0) 에서만 표시 되는 변수를 찾습니다.

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## PARAMETERS

### -제외

이 cmdlet이 작업에서 제외 하는 항목의 배열을 지정 합니다.
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

### -포함

다른 모든 항목을 제외 하 고 cmdlet이 동작 하는 항목의 배열을 지정 합니다.
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

변수의 이름을 지정합니다.
와일드카드가 지원됩니다.
변수 이름을로 파이프 할 수도 있습니다 `Get-Variable` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -범위

범위에 있는 변수를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **Global**
- **로컬**
- **스크립트**
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)

**Local** 이 기본값입니다.
자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

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

### -ValueOnly

이 cmdlet은 변수의 값만 가져옵니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

변수 이름이 포함 된 문자열을로 파이프 할 수 있습니다 `Get-Variable` .

## 출력

### System.object입니다.

이 cmdlet은 가져온 각 변수에 대해 **system.object** 를 반환 합니다. 개체 유형은 변수에 따라 달라집니다.

### System.object []

**Valueonly** 매개 변수를 지정 하는 경우 지정 된 변수의 값이 컬렉션인 경우는를 `Get-Variable` 반환 `[System.Object[]]` 합니다. 이 동작은 일반 파이프라인 작업에서 변수의 값을 한 번에 하나씩 처리 하는 것을 방지 합니다. 컬렉션 열거를 강제 적용 하는 방법은 명령을 괄호로 묶는 것입니다 `Get-Variable` .

## 참고

- 이 명령은 환경 변수를 관리하지 않습니다. 환경 변수를 관리하기 위해 환경 변수 공급자를 사용할 수 있습니다.

## 관련 링크

[Clear-Variable](Clear-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
