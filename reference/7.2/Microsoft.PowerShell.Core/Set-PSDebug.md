---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 45764b09bfa1f632fe5c36ca76b32b4a1b54874c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602448"
---
# Set-PSDebug

## 개요
스크립트 디버깅 기능을 설정/해제하고 추적 수준을 설정하며 Strict 모드를 전환합니다.

## SYNTAX

### on

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### 끄기

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## 설명

`Set-PSDebug`Cmdlet은 스크립트 디버깅 기능을 설정 및 해제 하 고 추적 수준을 설정 하며 strict 모드를 전환 합니다. 기본적으로 PowerShell 디버그 기능은 해제 되어 있습니다.

**Trace** 매개 변수의 값이 `1` 이면 스크립트의 각 줄이 실행 될 때 추적 됩니다. 매개 변수에 값 `2` , 변수 할당, 함수 호출 및 스크립트 호출도 추적 됩니다. **Step** 매개 변수를 지정 하면 스크립트의 각 줄이 실행 되기 전에 메시지가 표시 됩니다.

## 예제

### 예제 1: 추적 수준 설정

이 예에서는 추적 수준을으로 설정한 `2` 다음 숫자 1, 2 및를 표시 하는 스크립트를 실행 합니다.
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### 예제 2: 단계별 실행 설정

이 예에서는 단계별 실행을 설정한 다음 숫자 1, 2, 3을 표시 하는 스크립트를 실행 합니다.

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### 예제 3: strict 모드 사용

이 예에서는 PowerShell을 strict 모드로 전환 하 고 할당 된 값이 없는 변수에 액세스 하려고 합니다.

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### 예제 4: 디버그 기능 해제

이 예제에서는 모든 디버깅 기능을 해제 한 다음 숫자 1, 2, 3을 표시 하는 스크립트를 실행 합니다.

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## PARAMETERS

### -꺼짐

모든 스크립트 디버깅 기능을 해제합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -단계

단계별 스크립트 실행을 설정합니다. PowerShell은 각 줄을 실행 하기 전에 스크립트의 상태를 검사 하기 위해 새 인터프리터 수준을 중지 하거나, 계속 하거나, 입력 하 라는 메시지를 표시 합니다.

**Step** 매개 변수를 지정 하면의 추적 수준이 자동으로 설정 `1` 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

변수에 값을 할당 하 여 스크립트에서 참조 하도록 지정 합니다. 값이 할당 되기 전에 변수가 참조 되는 경우 PowerShell은 예외 오류를 반환 합니다. `Set-StrictMode -Version 1`와 같습니다. 자세한 내용은 [set-strictmode](Set-StrictMode.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trace

스크립트의 각 줄에 대 한 추적 수준을 지정 합니다. 각 줄은 실행 될 때 추적 됩니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 0: 스크립트 추적을 해제 합니다.
- 1: 실행 되는 스크립트 줄을 추적 합니다.
- 2: 스크립트 줄, 변수 할당, 함수 호출 및 스크립트를 추적 합니다.

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 대 한 입력을 파이프라인으로 지정할 수 없습니다.

## 출력

### 없음

이 cmdlet은 출력을 반환 하지 않습니다.

## 참고

## 관련 링크

[about_Debuggers](./About/about_Debuggers.md)

[Debug-Process](../Microsoft.PowerShell.Management/Debug-Process.md)

[Set-PSBreakpoint](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[Set-StrictMode](Set-StrictMode.md)

[Write-Debug](../Microsoft.PowerShell.Utility/Write-Debug.md)

