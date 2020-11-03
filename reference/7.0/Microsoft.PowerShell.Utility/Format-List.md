---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: df013bd6efd127a022d6bd41c5ea5fcca90dbc4a
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219337"
---
# Format-List

## 개요
출력의 형식을 각 속성이 새 줄에 표시되는 속성 목록으로 지정합니다.

## SYNTAX

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## 설명

`Format-List`Cmdlet은 명령의 출력 형식을 각 속성이 별도의 줄에 표시 되는 속성 목록으로 지정 합니다. `Format-List`를 사용 하 여 개체의 모든 속성 또는 선택한 속성을 목록 형식으로 표시 하 고 표시할 수 있습니다 (형식 목록 *).

목록의 각 항목에 사용 가능한 공간이 테이블 보다 더 많은 경우 PowerShell은 목록에 개체의 속성을 더 많이 표시 하 고 속성 값은 잘릴 가능성이 낮습니다.

## 예제

### 예제 1: 컴퓨터 서비스 포맷

```powershell
Get-Service | Format-List
```

이 명령은 컴퓨터의 서비스에 대한 정보를 목록 형식으로 지정합니다. 기본적으로 서비스는 테이블 형식으로 지정됩니다. `Get-Service`Cmdlet은 컴퓨터의 서비스를 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)가 파이프라인을 통해 결과를에 전달 합니다 `Format-List` .
그런 다음 `Format-List` 목록에서 서비스 정보의 형식을 지정 하 고 표시를 위해 기본 출력 cmdlet으로 보냅니다.

### 예제 2: TYPES.PS1XML 파일 서식 지정

이러한 명령은 PowerShell 디렉터리의 TYPES.PS1XML 파일에 대 한 정보를 목록으로 표시 합니다.

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

첫 번째 명령은 파일을 나타내는 개체를 가져와 변수에 저장 합니다 `$A` .

두 번째 명령은 `Format-List` 를 사용 하 여에 저장 된 개체에 대 한 정보를 형식으로 지정 합니다 `$A` . 이 명령은 **InputObject** 매개 변수를 사용 하 여 변수를에 전달 `Format-List` 합니다. 그러면에서 표시를 위해 형식이 지정 된 출력을 기본 출력 cmdlet으로 보냅니다.

### 예제 3: 이름을 기준으로 프로세스 속성 서식 지정

이 명령은 컴퓨터에 있는 각 프로세스의 이름, 기본 우선 순위 및 우선 순위 클래스를 표시합니다.

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

Cmdlet을 사용 하 여 `Get-Process` 각 프로세스를 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)가 파이프라인을 통해 프로세스 개체를에 전달 합니다 `Format-List` . `Format-List` 프로세스의 형식을 지정 된 속성 목록으로 지정 합니다. *속성* 매개 변수 이름은 선택 사항 이므로 생략할 수 있습니다.

### 예제 4: 프로세스의 모든 속성 서식 지정

이 명령은 Winlogon 프로세스의 모든 속성을 표시합니다.

```powershell
Get-Process winlogon | Format-List -Property *
```

Get-Process cmdlet을 사용하여 Winlogon 프로세스를 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)가 파이프라인을 통해 Winlogon 프로세스 개체를에 전달 합니다 `Format-List` . 이 명령은 *Property* 매개 변수를 사용 하 여 속성을 지정 하 고를 사용 하 여 \* 모든 속성을 표시 합니다.
*Property* 매개 변수의 이름은 선택 사항 이므로 생략 하 고 명령을 입력할 수 있습니다 `Format-List *` . `Format-List` 표시를 위해 결과를 기본 출력 cmdlet으로 자동으로 보냅니다.

### 예 5: 형식 오류 문제 해결

다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -DisplayError

이 cmdlet이 명령줄에서 오류를 표시 함을 나타냅니다. 이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-List` .

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

### -확장

컬렉션에 있는 개체 뿐만 아니라 서식이 지정 된 컬렉션 개체를 지정 합니다. 이 매개 변수는 ICollection(System.Collections) 인터페이스를 지원하는 개체의 형식을 지정할 수 있습니다. 기본값은 EnumOnly입니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- EnumOnly. 컬렉션에 있는 개체의 속성을 표시합니다.
- CoreOnly. 컬렉션 개체의 속성을 표시합니다.
- 둘 다. 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 cmdlet이 모든 오류 정보를 표시 함을 나타냅니다. **Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다. 기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.

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

### -GroupBy

공유 속성이 나 값에 따라 그룹의 출력을 지정 합니다. 출력의 식이나 속성을 입력하세요.

**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 이름 (또는 레이블)- `<string>`
- 식 `<string>` 또는 `<script block>`
- FormatString `<string>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

형식을 지정할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

### -속성

표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.
와일드카드가 지원됩니다.

이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다. "Property" 매개 변수 이름은 선택 사항입니다. 동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 이름 (또는 레이블)- `<string>`
- 식 `<string>` 또는 `<script block>`
- FormatString `<string>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

Cmdlet이 파이프라인을 통해 오류를 보내도록 지정 합니다. 이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-List` .

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

### -보기

대체 목록 형식 또는 보기의 이름을 지정 합니다. 동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체를로 파이프 할 수 있습니다 `Format-List` .

## 출력

### Microsoft. PowerShell. Internal. Format

`Format-List` 목록을 나타내는 형식 개체를 반환 합니다.

## 참고

기본 제공 별칭인 FL로 Format-List을 참조할 수도 있습니다. 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

와 같은 형식 cmdlet은 `Format-List` 표시할 데이터를 정렬 하지만 표시 하지는 않습니다.
데이터는 PowerShell의 출력 기능 및 Out 동사 (Out cmdlet)를 포함 하는 cmdlet (예: 또는)에 의해 표시 됩니다 `Out-Host` `Out-File` .

Format cmdlet을 사용 하지 않는 경우 PowerShell은 표시 하는 각 개체에 대해 기본 형식을 적용 합니다.

**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다. 를 사용 하 여 개체를 그룹화 하기 전에 Sort-Object `Format-List` 을 사용 합니다.

**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식을 지정할 수 있습니다. PowerShell 디렉터리의 파일에 정의 된 뷰를 사용 `*.format.PS1XML` 하거나 새 types.ps1xml 파일에서 고유한 뷰를 만들고 Update-FormatData cmdlet을 사용 하 여 powershell에 포함할 수 있습니다.

**View** 매개 변수의 대체 보기는 목록 형식을 사용 해야 합니다. 그렇지 않으면 명령이 실패 합니다. 대체 뷰가 테이블인 경우를 사용 `Format-Table` 합니다. 대체 뷰가 목록이 나 테이블이 아닌 경우를 사용 `Format-Custom` 합니다.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
