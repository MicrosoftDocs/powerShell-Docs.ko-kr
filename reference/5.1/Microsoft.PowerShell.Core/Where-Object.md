---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: aaee09926c93bb8c8e72efb5fd4ea34e2fc67391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212681"
---
# Where-Object

## 개요
속성 값에 따라 컬렉션에서 개체를 선택합니다.

## SYNTAX

### EqualSet (기본값)

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ] [<CommonParameters>]
```

### ScriptBlockSet

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### MatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Match]
 [<CommonParameters>]
```

### CaseSensitiveEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CEQ] [<CommonParameters>]
```

### NotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NE] [<CommonParameters>]
```

### CaseSensitiveNotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNE] [<CommonParameters>]
```

### GreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GT] [<CommonParameters>]
```

### CaseSensitiveGreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGT] [<CommonParameters>]
```

### LessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LT] [<CommonParameters>]
```

### CaseSensitiveLessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLT] [<CommonParameters>]
```

### GreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GE] [<CommonParameters>]
```

### CaseSensitiveGreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGE] [<CommonParameters>]
```

### LessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LE] [<CommonParameters>]
```

### CaseSensitiveLessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLE] [<CommonParameters>]
```

### LikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Like] [<CommonParameters>]
```

### CaseSensitiveLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLike] [<CommonParameters>]
```

### NotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotLike] [<CommonParameters>]
```

### CaseSensitiveNotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotLike]
 [<CommonParameters>]
```

### CaseSensitiveMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CMatch] [<CommonParameters>]
```

### NotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotMatch]
 [<CommonParameters>]
```

### CaseSensitiveNotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotMatch]
 [<CommonParameters>]
```

### ContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Contains]
 [<CommonParameters>]
```

### CaseSensitiveContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CContains]
 [<CommonParameters>]
```

### NotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotContains]
 [<CommonParameters>]
```

### CaseSensitiveNotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotContains]
 [<CommonParameters>]
```

### 오목

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-In] [<CommonParameters>]
```

### CaseSensitiveInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CIn] [<CommonParameters>]
```

### NotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotIn] [<CommonParameters>]
```

### CaseSensitiveNotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotIn] [<CommonParameters>]
```

### IsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Is] [<CommonParameters>]
```

### IsNotSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-IsNot] [<CommonParameters>]
```

## 설명

`Where-Object`Cmdlet은 전달 되는 개체의 컬렉션에서 특정 속성 값이 있는 개체를 선택 합니다. 예를 들어 cmdlet을 사용 하 여 특정 `Where-Object` 날짜 이후에 만들어진 파일, 특정 ID를 가진 이벤트 또는 특정 버전의 Windows를 사용 하는 컴퓨터를 선택할 수 있습니다.

Windows PowerShell 3.0부터 명령을 생성 하는 방법에는 두 가지가 있습니다 `Where-Object` .

- **스크립트 블록** 입니다. 스크립트 블록을 사용하여 속성 이름, 비교 연산자 및 속성 값을 지정할 수 있습니다. `Where-Object` 스크립트 블록 문이 true 인 모든 개체를 반환 합니다.

  예를 들어 다음 명령은 일반적인 우선 순위 클래스, 즉 **PriorityClass** 속성 값이 normal 인 프로세스의 프로세스를 가져옵니다.

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  모든 PowerShell 비교 연산자는 스크립트 블록 형식에서 유효 합니다. 비교 연산자에 대 한 자세한 내용은 [about_Comparison_Operators](./About/about_Comparison_Operators.md)를 참조 하세요.

- **Comparison 문** 입니다. 또한 자연어와 더욱 유사하게 비교문을 작성할 수도 있습니다. 비교문은 Windows PowerShell 3.0에서 도입되었습니다.

  예를 들어 다음 명령은 Normal의 우선 순위 클래스를 포함 하는 프로세스를 가져옵니다. 이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  Windows PowerShell 3.0부터, `Where-Object` 명령에서 비교 연산자를 매개 변수로 추가 `Where-Object` 합니다. 지정되지 않은 경우 모든 연산자는 대/소문자를 구분하지 않습니다. Windows PowerShell 3.0 이전에는 PowerShell 언어의 비교 연산자를 스크립트 블록에만 사용할 수 있습니다.

에 단일 **속성** 을 제공 하면 `Where-Object` 속성의 값이 부울 식으로 처리 됩니다. **Length** 값이 0이 아니면 식이 **True** 로 평가 됩니다. `('hi', '', 'there') | Where-Object Length`

이전 예제는와 기능적으로 동일 합니다.

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## 예제

### 예제 1: 중지 된 서비스 가져오기

이러한 명령은 현재 중지 된 모든 서비스 목록을 가져옵니다. `$_`자동 변수는 cmdlet에 전달 되는 각 개체를 나타냅니다 `Where-Object` .

첫 번째 명령은 스크립트 블록 형식을 사용 하 고 두 번째 명령은 비교 문 형식을 사용 합니다. 이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### 예제 2: 작업 집합을 기반으로 프로세스 가져오기

이 명령은 작업 집합이 250 메가바이트 (KB) 보다 큰 프로세스를 나열 합니다. Scriptblock 및 문 구문은 동일 하며 서로 바꿔 사용할 수 있습니다.

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### 예제 3: 프로세스 이름에 따라 프로세스 가져오기

이러한 명령은 문자로 시작 하는 **ProcessName** 속성 값을 가진 프로세스를 가져옵니다 `p` . **Match** 연산자를 사용 하면 정규식 일치 항목을 사용할 수 있습니다.

Scriptblock 및 문 구문은 동일 하며 서로 바꿔 사용할 수 있습니다.

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### 예제 4: 비교 문 형식 사용

이 예에서는 cmdlet의 새 비교 문 형식을 사용 하는 방법을 보여 줍니다 `Where-Object` .

첫 번째 명령은 비교문의 형식을 사용합니다.
이 명령에서 별칭은 사용되지 않고 모든 매개 변수는 매개 변수 이름을 포함합니다.

두 번째 명령은 비교 명령 형식의 더 자연스러운 용례입니다. `where`별칭은 cmdlet 이름으로 대체 `Where-Object` 되 고 모든 선택적 매개 변수 이름은 생략 됩니다.

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### 예 5: 속성을 기반으로 명령 가져오기

이 예제에서는 true 또는 false 항목을 반환하거나 지정된 속성 값을 포함하는 명령을 작성하는 방법을 보여 줍니다. 각 예제에는 명령에 대 한 스크립트 블록과 비교 문 형식이 모두 나와 있습니다.

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### 예제 6: 여러 조건 사용

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

이 예제에서는 `Where-Object` 여러 조건을 사용 하 여 명령을 만드는 방법을 보여 줍니다.

이 명령은 업데이트할 수 있는 도움말 기능을 지원하는 중요하지 않은 모듈을 가져옵니다. 이 명령은 cmdlet의 **ListAvailable** 매개 변수를 사용 하 여 `Get-Module` 컴퓨터의 모든 모듈을 가져옵니다. 파이프라인 연산자 ()는 모듈을 `|` cmdlet으로 보냅니다 .이 `Where-Object` cmdlet은 이름이 MICROSOFT 또는 PS로 시작 하지 않는 모듈을 가져오고, 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 있는 위치를 PowerShell에 알리는 **HelpInfoURI** 속성 값을 포함 합니다. 비교 문은 **And** 논리 연산자로 연결 됩니다.

이 예제에서는 스크립트 블록 명령 형식을 사용합니다. **And** 및 **Or** 와 같은 논리 연산자는 스크립트 블록 에서만 유효 합니다. 명령의 비교 문 형식으로는 사용할 수 없습니다 `Where-Object` .

- PowerShell 논리 연산자에 대 한 자세한 내용은 [about_Logical_Operators](./About/about_logical_operators.md)를 참조 하세요.
- 업데이트할 수 있는 도움말 기능에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.

## PARAMETERS

### -CContains

이 cmdlet은 개체의 속성 값이 지정 된 값과 정확히 일치 하는 경우 컬렉션에서 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

`Get-Process | where ProcessName -CContains "svchost"`

**Ccontains** 는 값의 컬렉션을 참조 하 고, 지정 된 값과 정확히 일치 하는 항목이 컬렉션에 포함 되어 있으면 true입니다. 입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CEQ

이 cmdlet이 속성 값이 지정 된 값과 같은 경우 해당 개체를 가져옵니다.
이 작업은 대/소문자를 구분 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGE

이 cmdlet이 속성 값이 지정 된 값 보다 크거나 같은 경우 해당 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGT

이 cmdlet이 속성 값이 지정 된 값 보다 큰 경우 해당 개체를 가져옵니다.
이 작업은 대/소문자를 구분 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CIn

속성 값이 지정 된 값을 포함 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다. 이 작업은 대/소문자를 구분 합니다.

`Get-Process | where -Value "svchost" -CIn ProcessName`

**Cin** 은 속성 및 값 위치가 반전 된다는 점을 제외 하 고는 **cin** 와 유사 합니다. 예를 들어 다음 문은 모두 true입니다.

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLE

이 cmdlet이 속성 값이 지정 된 값 보다 작거나 같은 경우 해당 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLike

속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하는 경우이 cmdlet이 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

`Get-Process | where ProcessName -CLike "*host"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLT

이 cmdlet이 속성 값이 지정 된 값 보다 작은 경우 해당 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CMatch

속성 값이 지정 된 정규식과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다. 이 작업은 대/소문자를 구분 합니다. 입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.

`Get-Process | where ProcessName -CMatch "Shell"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNE

속성 값이 지정 된 값과 다른 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.
이 작업은 대/소문자를 구분 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotContains

이 cmdlet은 개체의 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

`Get-Process | where ProcessName -CNotContains "svchost"`

**Notcontains** 및 **cnotcontains** 는 값의 컬렉션을 참조 하 고 컬렉션에 지정 된 값과 정확히 일치 하는 항목이 포함 되지 않은 경우 true입니다. 입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotIn

이 cmdlet은 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

`Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`

**Notin** 및 **cnotin** 연산자는 속성 및 값 위치가 반전 된다는 점을 제외 하 고 **Notin** 및 **cnotin** 와 비슷합니다. 예를 들어 다음 문은 true입니다.

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotLike

이 cmdlet은 속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하지 않는 경우 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다.

`Get-Process | where ProcessName -CNotLike "*host"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotMatch

이 cmdlet은 속성 값이 지정 된 정규식과 일치 하지 않는 경우 해당 개체를 가져옵니다. 이 작업은 대/소문자를 구분 합니다. 입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.

`Get-Process | where ProcessName -CNotMatch "Shell"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -포함

개체의 속성 값에 있는 항목이 지정 된 값과 정확히 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.

`Get-Process | where ProcessName -Contains "Svchost"`

속성 값이 단일 개체를 포함 하는 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EQ

이 cmdlet이 속성 값이 지정 된 값과 같은 경우 해당 개체를 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterScript

개체를 필터링하는 데 사용되는 스크립트 블록을 지정합니다. 스크립트 블록을 중괄호 ()로 묶습니다 `{}` .

매개 변수 이름 **Filterscript** 는 선택 사항입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GE

이 cmdlet이 속성 값이 지정 된 값 보다 크거나 같은 경우 해당 개체를 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GT

이 cmdlet이 속성 값이 지정 된 값 보다 큰 경우 해당 개체를 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -In

속성 값이 지정 된 값과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.
다음은 그 예입니다. 

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

**값** 매개 변수 값이 단일 개체인 경우 PowerShell은이를 하나의 개체의 컬렉션으로 변환 합니다.

개체의 속성 값이 배열인 경우 PowerShell은 참조 같음을 사용 하 여 일치 하는 항목을 확인 합니다. `Where-Object`**Property** 매개 변수의 값과 **값** 의 값이 개체의 동일한 인스턴스인 경우에만 개체를 반환 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

필터링할 개체를 지정합니다. 개체를로 파이프 할 수도 있습니다 `Where-Object` .

에 **inputobject** 매개 변수를 사용 하는 경우 `Where-Object` 명령 결과를로 파이프 하는 대신 `Where-Object` **inputobject** 값은 단일 개체로 처리 됩니다. 이는 값이 명령 결과인 컬렉션 (예:) 인 경우에도 마찬가지입니다 `-InputObject (Get-Process)` . **InputObject** 는 배열 또는 개체 컬렉션의 개별 속성을 반환할 수 없으므로를 사용 하 여 `Where-Object` 정의 된 속성에 특정 값이 있는 개체에 대 한 개체의 컬렉션을 필터링 하는 경우 `Where-Object` 이 항목의 예제에 나와 있는 것 처럼 파이프라인에서를 사용 하는 것이 좋습니다.

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

### -Is

이 cmdlet은 속성 값이 지정 된 .NET 형식의 인스턴스인 경우 개체를 가져옵니다. 유형 이름은 대괄호로 묶으세요.

예를 들어 `Get-Process | where StartTime -Is [DateTime]`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IsNot

이 cmdlet이 속성 값이 지정 된 .NET 형식의 인스턴스가 아닌 경우 해당 개체를 가져옵니다.

예를 들어 `Get-Process | where StartTime -IsNot [DateTime]`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LE

이 cmdlet이 속성 값이 지정 된 값 보다 작거나 같은 경우 해당 개체를 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -좋아요

속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하는 경우이 cmdlet이 개체를 가져옵니다.

`Get-Process | where ProcessName -Like "*host"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LT

이 cmdlet이 속성 값이 지정 된 값 보다 작은 경우 해당 개체를 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Match

속성 값이 지정 된 정규식과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다. 입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.

`Get-Process | where ProcessName -Match "shell"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NE

속성 값이 지정 된 값과 다른 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotContains

속성 값에 지정 된 값과 정확히 일치 하는 항목이 없는 경우이 cmdlet이 개체를 가져옵니다.

`Get-Process | where ProcessName -NotContains "Svchost"`

**Notcontains** 는 값의 컬렉션을 참조 하며, 지정 된 값과 정확히 일치 하는 항목이 컬렉션에 포함 되어 있지 않으면 true입니다. 입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotIn

이 cmdlet은 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.

`Get-Process | where -Value "svchost" -NotIn -Property ProcessName`

**Value** 값이 단일 개체 이면 PowerShell은이를 한 개체의 컬렉션으로 변환 합니다.

개체의 속성 값이 배열인 경우 PowerShell은 참조 같음을 사용 하 여 일치 하는 항목을 확인 합니다. `Where-Object`**속성** 값과 **값** 값이 개체의 동일한 인스턴스가 아닌 경우에만 개체를 반환 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotLike

이 cmdlet은 속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하지 않는 경우 개체를 가져옵니다.

`Get-Process | where ProcessName -NotLike "*host"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotMatch

이 cmdlet이 속성 값이 지정 된 정규식과 일치 하지 않는 경우 해당 개체를 가져옵니다. 입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.

`Get-Process | where ProcessName -NotMatch "PowerShell"`

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

object 속성의 이름을 지정합니다. 매개 변수 이름 **속성** 은 선택 사항입니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

속성 값을 지정합니다. 매개 변수 이름 **값** 은 선택 사항입니다. 이 매개 변수는 다음 비교 매개 변수와 함께 사용할 경우 와일드 카드 문자를 허용 합니다.

- **CLike**
- **CNotLike**
- **이와**
- **NotLike**

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Object
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### Object

이 cmdlet은 입력 개체 집합에서 선택한 항목을 반환 합니다.

## 참고

Windows PowerShell 4.0부터 `Where` `ForEach` 컬렉션과 함께 사용 하기 위해 메서드가 추가 되었습니다.

이러한 새 메서드에 대 한 자세한 내용은 여기를 참조 하세요 [about_arrays](./About/about_Arrays.md)

## 관련 링크

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[ForEach-Object](ForEach-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)
