---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: 8773c69d638a1d04dc946cf448a44799341e663b
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390595"
---
# Set-StrictMode

## 개요
식, 스크립트 및 스크립트 블록에서 코딩 규칙을 설정하고 적용합니다.

## SYNTAX

### Version (기본값)

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### 끄기

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## 설명

`Set-StrictMode`Cmdlet은 현재 범위와 모든 자식 범위에 대해 strict 모드를 구성 하 고 설정 및 해제 합니다. Strict 모드가 on 인 경우 식, 스크립트 또는 스크립트 블록의 내용이 기본 모범 사례 코딩 규칙을 위반 하면 PowerShell에서 종료 오류를 생성 합니다.

**Version** 매개 변수를 사용 하 여 적용 되는 코딩 규칙을 결정 합니다.

`Set-PSDebug -Strict` cmdlet은 전역 범위에 대해 strict 모드를 설정 합니다. `Set-StrictMode` 현재 범위와 해당 하위 범위에만 영향을 줍니다. 따라서 스크립트나 함수에서이 함수를 사용 하 여 전역 범위에서 상속 된 설정을 재정의할 수 있습니다.

`Set-StrictMode`가 off 인 경우 PowerShell은 다음과 같은 동작을 수행 합니다.

- 초기화 되지 않은 변수는 `$Null` 형식에 따라 0 또는 값을 갖는 것으로 간주 됩니다.
- 존재 하지 않는 속성에 대 한 참조가 반환 됩니다. `$Null`
- 잘못 된 함수 구문의 결과는 오류 조건에 따라 다릅니다.
- 배열의 잘못 된 인덱스를 사용 하 여 값을 검색 하려고 하면이 반환 됩니다. `$Null`

## 예제

### 예제 1: strict 모드를 버전 1.0로 설정

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
InvalidOperation: The variable '$a' cannot be retrieved because it has not been set.
```

Strict 모드를 버전 1.0로 설정 하면 초기화 되지 않은 변수를 참조 하려는 시도가 실패 합니다.

### 예제 2: strict 모드를 버전 2.0로 설정

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
InvalidOperation: The function or command was called as if it were a method. Parameters should be separated by spaces. For information about parameters, see the about_Parameters Help topic.
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
PropertyNotFoundException: The property 'Month' cannot be found on this object. Verify that the property exists.
```

이 명령은 strict 모드를 켜고 버전 2.0으로 설정합니다. 따라서 함수 호출에 대해 괄호와 쉼표를 사용 하는 메서드 구문을 사용 하거나 초기화 되지 않은 변수나 존재 하지 않는 속성을 참조 하는 경우 PowerShell에서 오류를 반환 합니다.

샘플 출력은 버전 2.0 strict 모드의 결과를 보여 줍니다.

버전 2.0 strict 모드를 사용하지 않으면 "(3,4)" 값은 아무것도 추가되지 않은 단일 배열 개체로 해석됩니다. 버전 2.0 strict 모드를 사용 하면 두 값을 제출 하는 잘못 된 구문으로 올바르게 해석 됩니다.

버전 2.0을 사용 하지 않으면 문자열의 존재 하지 않는 **Month** 속성에 대 한 참조는만 반환 `$Null` 합니다. 버전 2.0을 사용 하면 참조 오류로 올바르게 해석 됩니다.

### 예제 3: strict 모드를 버전 3.0로 설정

Strict 모드가 **Off** 로 설정 된 경우 범위를 벗어난 인덱스 결과는 null 값을 반환 합니다.

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
OperationStopped: Index was outside the bounds of the array.

InvalidArgument: Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
```

Strict 모드가 버전 3 이상으로 설정 되 면 범위를 잘못 되었거나 범위를 벗어난 인덱스에서 오류가 발생 합니다.

## PARAMETERS

### -꺼짐

이 cmdlet이 현재 범위와 모든 자식 범위에 대해 strict 모드를 해제 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

strict 모드에서 오류를 발생시키는 조건을 지정합니다. 이 매개 변수는 유효한 PowerShell 버전 번호를 모두 허용 합니다. 3 보다 큰 숫자는 모두 **최신** 으로 처리 됩니다.

이 매개 변수에 유효한 값은 다음과 같습니다.

- 1.0
  - 문자열에서 초기화 되지 않은 변수를 제외 하 고 초기화 되지 않은 변수에 대 한 참조를 금지 합니다.
- 2.0
  - 초기화 되지 않은 변수에 대 한 참조를 금지 합니다. 여기에는 문자열에 초기화 되지 않은 변수가 포함 됩니다.
  - 개체의 존재 하지 않는 속성에 대 한 참조를 금지 합니다.
  - 메서드를 호출 하는 구문을 사용 하는 함수 호출을 금지 합니다.
- 3.0
  - 초기화 되지 않은 변수에 대 한 참조를 금지 합니다. 여기에는 문자열에 초기화 되지 않은 변수가 포함 됩니다.
  - 개체의 존재 하지 않는 속성에 대 한 참조를 금지 합니다.
  - 메서드를 호출 하는 구문을 사용 하는 함수 호출을 금지 합니다.
  - 범위를 벗어났거나 확인할 수가 없는 배열 인덱스를 금지 합니다.
- 최신
  - 사용 가능한 최신 버전을 선택 합니다. 최신 버전은 가장 엄격 합니다. 새 버전이 PowerShell에 추가 되는 경우에도 스크립트에서 사용 가능한 가장 엄격한 버전을 사용 하는지 확인 하려면이 값을 사용 합니다.

> [!CAUTION]
> 스크립트에서 **최신** **버전** 을 사용 합니다. **최신** 의 의미는 PowerShell의 새 릴리스에서 변경 될 수 있습니다. 따라서를 사용 하는 이전 버전의 PowerShell 용으로 작성 된 스크립트는 `Set-StrictMode -Version Latest` 최신 버전의 powershell에서 실행 될 때 더 제한적인 규칙이 적용 됩니다.

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

`Set-StrictMode` 는 설정 된 범위와 해당 하위 범위에만 적용 됩니다. PowerShell의 범위에 대 한 자세한 내용은 [about_Scopes](about/about_Scopes.md)를 참조 하세요.

## 관련 링크

[Set-PSDebug](Set-PSDebug.md)
