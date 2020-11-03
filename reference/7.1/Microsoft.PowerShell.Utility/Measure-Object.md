---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 88b18a929a1debc85eb7ce65dbdf2d14fc4b89cd
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219273"
---
# Measure-Object

## 개요
개체의 숫자 속성과 텍스트 파일 등 문자열 개체의 문자, 단어 및 줄을 계산합니다.

## SYNTAX

### GenericMeasure (기본값)

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### TextMeasure

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## 설명

`Measure-Object`Cmdlet은 특정 개체 유형의 속성 값을 계산 합니다.
`Measure-Object` 는 명령의 매개 변수에 따라 세 가지 유형의 측정을 수행 합니다.

`Measure-Object`Cmdlet은 개체의 속성 값에 대 한 계산을 수행 합니다. `Measure-Object`를 사용 하 여 개체 수를 계산 하거나 지정 된 **속성** 을 사용 하 여 개체를 계산할 수 있습니다. 를 사용 하 여 `Measure-Object` 숫자 값의 **최소값** , **최대값** , **합계** , **standarddeviation** 및 **평균** 을 계산할 수도 있습니다. **문자열** 개체의 경우를 사용 하 여 `Measure-Object` 줄, 단어 및 문자 수를 계산할 수도 있습니다.

## 예제

### 예 1: 디렉터리에서 파일 및 폴더 수 계산

이 명령은 현재 디렉터리의 파일 및 폴더 수를 계산합니다.

```powershell
Get-ChildItem | Measure-Object
```

### 예 2: 디렉터리에서 파일 측정

이 명령은 현재 디렉터리에 있는 모든 파일 크기의 **최소값** , **최대값** 및 **합계** 와 디렉터리에 있는 파일의 평균 크기를 표시 합니다.

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### 예 3: 텍스트 파일의 측정 텍스트

이 명령은 Text.txt 파일의 문자, 단어 및 줄 수를 표시합니다.
**원시** 매개 변수가 없으면은 `Get-Content` 파일을 줄의 배열로 출력 합니다.

첫 번째 명령은 `Set-Content` 를 사용 하 여 일부 기본 텍스트를 파일에 추가 합니다.

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### 예 4: 지정 된 속성을 포함 하는 측정값 개체

이 예에서는 **DisplayName** 속성이 있는 개체의 수를 계산 합니다. 처음 두 명령은 로컬 컴퓨터의 모든 서비스 및 프로세스를 검색 합니다. 세 번째 명령은 서비스와 프로세스의 조합 수를 계산 합니다. 마지막 명령은 두 개의 컬렉션을 결합 하 고 결과를로 파이프 합니다 `Measure-Object` .

**System.object** 개체에 **DisplayName** 속성이 없으며 최종 카운트를 벗어난 경우입니다.

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### 예 5: CSV 파일의 내용 측정

이 명령은 회사 직원의 평균 근무 기간(년)을 계산합니다.

`ServiceYrs.csv`이 파일은 직원 번호와 각 직원의 서비스 연도를 포함 하는 CSV 파일입니다. 테이블의 첫 번째 행은 **EmpNo** , **Years** 의 머리글 행입니다.

를 사용 하 여 `Import-Csv` 파일을 가져올 때 결과는 **EmpNo** 및 **Years** 의 note 속성이 있는 **PSCustomObject** 입니다.
`Measure-Object`를 사용 하 여 개체의 다른 속성과 마찬가지로 이러한 속성의 값을 계산할 수 있습니다.

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### 예 6: 부울 값 측정

이 예제에서는가 부울 값을 측정 하는 방법을 보여 줍니다 `Measure-Object` .
이 경우 **PSIsContainer** **Boolean** 속성을 사용 하 여 현재 디렉터리에서 폴더 (vs. 파일)의 발생을 측정 합니다.

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### 예 7: 측정값 문자열

다음 예에서는 줄의 수, 먼저 단일 문자열, 여러 문자열을 차례로 측정 합니다. 줄 바꿈 문자는 <code>`n</code> 문자열을 여러 줄로 구분 합니다.

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### 예 8: 모든 값 측정

PowerShell 6부터의 **Allstats** 매개 변수를 사용 하 여 `Measure-Object` 모든 통계를 함께 측정할 수 있습니다.

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### 예 9: scriptblock 속성을 사용 하 여 측정

PowerShell 6부터은 `Measure-Object` **ScriptBlock** 속성을 지원 합니다. 다음 예제에서는 **ScriptBlock** 속성을 사용 하 여 디렉터리에 있는 모든 파일의 크기 (mb)를 결정 하는 방법을 보여 줍니다.

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### 예 10: 측정값 해시 테이블

PowerShell 6부터 `Measure-Object` 은 **해시 테이블** 입력 측정을 지원 합니다. 다음 예에서는 `num` 3 개의 **해시 테이블** 개체의 키에 대 한 가장 큰 값을 결정 합니다.

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### 예 11: 표준 편차 측정

PowerShell 6부터 `Measure-Object` 은 `-StandardDeviation` 매개 변수를 지원 합니다. 다음 예에서는 모든 프로세스에서 사용 하는 CPU에 대 한 *표준 편차* 를 확인 합니다. 큰 편차는 대부분의 CPU를 사용 하는 적은 수의 프로세스를 의미 합니다.

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### 예 12: 와일드 카드를 사용 하 여 측정

PowerShell 6부터에서는 `Measure-Object` 속성 이름에 와일드 카드를 사용 하 여 개체 측정을 지원 합니다. 다음 예에서는 프로세스 집합에서 페이징 메모리 사용의 최대 크기를 확인 합니다.

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## PARAMETERS

### -평균

Cmdlet에서 지정 된 속성의 평균 값을 표시 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -문자

Cmdlet이 입력 개체의 문자 수를 계산 함을 나타냅니다.

> [!NOTE]
> **단어** , **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다. 예 7을 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWhiteSpace

Cmdlet이 문자 수의 공백을 무시 함을 나타냅니다.
기본적으로 공백은 무시되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

측정할 개체를 지정합니다.
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

에 **inputobject** 매개 변수를 사용 하는 경우 `Measure-Object` 명령 결과를로 파이프 하는 대신 `Measure-Object` **inputobject** 값은 단일 개체로 처리 됩니다.

`Measure-Object`개체의 정의 된 속성에 특정 값이 있는지 여부에 따라 개체의 컬렉션을 측정 하려면 파이프라인에서를 사용 하는 것이 좋습니다.

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

### -줄

Cmdlet이 입력 개체의 줄 수를 계산 함을 나타냅니다.

> [!NOTE]
> **단어** , **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다. 예 7을 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -최대

Cmdlet에서 지정 된 속성의 최대값을 표시 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -최소

Cmdlet에서 지정 된 속성의 최소값이 표시 됨을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

측정할 속성을 하나 이상 지정 합니다. 다른 측정값을 지정 하지 않으면에서 `Measure-Object` 지정한 속성을 가진 개체의 수를 계산 합니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록 이어야 합니다. 자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -StandardDeviation

Cmdlet에서 지정 된 속성 값의 표준 편차를 표시 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -합계

Cmdlet에서 지정 된 속성 값의 합계를 표시 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllStats

Cmdlet이 지정 된 속성의 모든 통계를 표시 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Word

Cmdlet이 입력 개체의 단어 수를 계산 함을 나타냅니다.

> [!NOTE]
> **단어** , **문자** 및 **줄** 스위치는 각 입력 개체 뿐만 아니라 입력 개체 *전체* 에도 *포함* 됩니다. 예 7을 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
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

### System.web. PSObject

개체를로 파이프 할 수 있습니다 `Measure-Object` .

## 출력

### 그러지 않으면 genericmeasureinfo.

### TextMeasureInfo.

**Word** 매개 변수를 사용 하는 경우 `Measure-Object` **TextMeasureInfo** 개체를 반환 합니다.
그렇지 않으면 **그러지 않으면 genericmeasureinfo** 개체를 반환 합니다.

## 참고

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
