---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 43958b376123202e152ceb2da3223cc2f22b0687
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96935904"
---
# Measure-Command

## 개요
스크립트 블록 및 cmdlet을 실행하는 데 걸리는 시간을 측정합니다.

## SYNTAX

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## 설명

`Measure-Command`Cmdlet은 작업 실행 시간을 지 나 스크립트 블록 또는 cmdlet을 내부적으로 실행 하 고 실행 시간을 반환 합니다.

> [!NOTE]
> 스크립트 블록은 `Measure-Command` 자식 범위가 아니라 현재 범위에서 실행 됩니다.

## 예제

### 예제 1: 명령 측정

이 예에서는 `Get-EventLog` Windows PowerShell 이벤트 로그에서 이벤트를 가져오는 명령을 실행 하는 데 걸리는 시간을 측정 합니다.

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### 예제 2: Measure-Command에서 두 출력 비교

첫 번째 명령은 `Get-ChildItem` **Path** 매개 변수를 사용 하 여 `.txt` `C:\Windows` 디렉터리 및 하위 디렉터리에 있는 파일만 가져오는 재귀 명령을 처리 하는 데 걸리는 시간을 측정 합니다.

두 번째 명령은 `Get-ChildItem` 공급자별 ' 매개 변수를 사용 하는 재귀 명령을 처리 하는 데 걸리는 시간을 측정 합니다.

이러한 명령은 PowerShell 명령에서 공급자별 필터를 사용 하는 값을 보여 줍니다.

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### 예제 3: Measure-Command에 입력 파이핑

파이프 된 개체는 `Measure-Command` **Expression** 매개 변수에 전달 되는 스크립트 블록에서 사용할 수 있습니다. 스크립트 블록은 파이프라인의 각 개체에 대해 한 번씩 실행 됩니다.

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### 예제 4: 측정 된 명령의 출력 표시

에서 식의 출력을 표시 하려면 `Measure-Command` 파이프를로 사용할 수 있습니다 `Out-Default` .

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### 예 5: 자식 범위에서 실행 측정

`Measure-Command` 현재 범위에서 스크립트 블록을 실행 하므로 스크립트 블록은 현재 범위의 값을 수정할 수 있습니다. 현재 범위를 변경 하지 않으려면 스크립트 블록을 중괄호 ()로 래핑하고 `{}` 호출 연산자 ()를 사용 `&` 하 여 자식 범위에서 블록을 실행 해야 합니다.

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

호출 연산자에 대 한 자세한 내용은 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)를 참조 하세요.

## PARAMETERS

### -식

시간이 측정되는 식을 지정합니다. 식을 중괄호 ()로 묶습니다 `{}` .

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

**InputObject** 매개 변수에 바인딩된 개체는 **Expression** 매개 변수에 전달 된 스크립트 블록의 선택적 입력입니다. 스크립트 블록 내에서를 `$_` 사용 하 여 파이프라인의 현재 개체를 참조할 수 있습니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

개체를로 파이프 할 수 있습니다 `Measure-Command` .

## 출력

### System.TimeSpan

`Measure-Command` 결과를 나타내는 시간 범위 개체를 반환 합니다.

## 참고

## 관련 링크

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Trace-Command](Trace-Command.md)

