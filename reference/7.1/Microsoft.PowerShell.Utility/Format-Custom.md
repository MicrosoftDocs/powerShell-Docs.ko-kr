---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: c8bf4dfa9077af04e4122672a15a7c768cb49ea2
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219258"
---
# Format-Custom

## 개요
사용자 지정된 보기를 사용하여 출력 형식을 지정합니다.

## SYNTAX

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## 설명

`Format-Custom`Cmdlet은 대체 보기에 정의 된 대로 명령의 출력 형식을 지정 합니다.
`Format-Custom` 는 단순히 테이블이 나 목록이 아닌 보기를 표시 하도록 설계 되었습니다. PowerShell에 정의 된 뷰를 사용 하거나 새 파일에서 고유한 뷰를 만들고 `format.ps1xml` cmdlet을 사용 `Update-FormatData` 하 여 powershell에 추가할 수 있습니다.

## 예제

### 예제 1: 사용자 지정 보기를 사용 하 여 출력 서식 지정

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

이 명령은 `Start-Transcript` 사용자가 만든 사용자 지정 보기 인 MyView 보기에 정의 된 형식으로 cmdlet에 대 한 정보를 지정 합니다. 이 명령을 성공적으로 실행 하려면 먼저 새 TYPES.PS1XML 파일을 만들고 **myview** 뷰를 정의한 다음 `Update-FormatData` 명령을 사용 하 여 Types.ps1xml 파일을 PowerShell에 추가 해야 합니다.

### 예제 2: 기본 보기를 사용 하 여 출력 서식 지정

```powershell
Get-Process Winlogon | Format-Custom
```

이 명령은 **Winlogon** 프로세스에 대 한 정보의 형식을 다른 사용자 지정 보기로 지정 합니다.
이 명령은 **View** 매개 변수를 사용 하지 않으므로는 `Format-Custom` 기본 사용자 지정 뷰를 사용 하 여 데이터의 형식을 지정 합니다.

### 예 3: 형식 오류 문제 해결

다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -깊이

표시에서 열의 개수를 지정합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayError

명령줄에 오류를 표시합니다. 이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Custom` .

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

컬렉션의 개체와 함께 컬렉션 개체의 형식을 지정합니다. 이 매개 변수는 **Collections** 인터페이스를 지 원하는 개체의 형식을 지정 하도록 디자인 되었습니다. 기본값은 **Enumonly** 입니다.

유효한 값은 다음과 같습니다.

- EnumOnly: 컬렉션에 있는 개체의 속성을 표시 합니다.
- CoreOnly: 컬렉션 개체의 속성을 표시 합니다.
- Both: 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

cmdlet에 모든 오류 정보를 표시하도록 지정합니다. **Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다. 기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.

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

공유 속성이나 값에 따라 그룹으로 출력 형식을 지정합니다. 출력의 식이나 속성을 입력하세요.

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

이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다. 매개 변수 이름 **속성** 은 선택 사항입니다. 동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 식 `<string>` 또는 `<script block>`
- 크기 `<int32>`

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

파이프라인을 통해 오류를 보냅니다. 이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Custom` .

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

대체 형식 또는 보기의 이름을 지정 합니다. 이 매개 변수를 생략 하면에서 `Format-Custom` 기본 사용자 지정 뷰를 사용 합니다. 동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

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

모든 개체를로 파이프 할 수 있습니다 `Format-Custom` .

## 출력

### Microsoft. PowerShell. Internal. Format

`Format-Custom` 표시를 나타내는 형식 개체를 반환 합니다.

## 참고

`Format-Custom` 는 단순히 테이블이 나 목록이 아닌 보기를 표시 하도록 설계 되었습니다. 대체 테이블 뷰를 표시 하려면를 사용 `Format-Table` 합니다. 대체 목록 보기를 표시 하려면를 사용 `Format-List` 합니다.

의 기본 제공 별칭인를 참조할 수도 있습니다 `Format-Custom` `fc` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다. 를 사용 하 여 개체를 그룹화 하기 전에를 `Format-Custom` 사용 하 여 개체를 `Sort-Object` 정렬 합니다.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
