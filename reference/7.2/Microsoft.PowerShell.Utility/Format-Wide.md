---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: ba61c2d24d85256c55a7409fc368de4407aad5a9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602438"
---
# Format-Wide

## 개요
개체를 각 개체의 한 속성만을 표시하는 넓은 표 형식으로 지정합니다.

## SYNTAX

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## 설명

`Format-Wide`Cmdlet은 각 개체의 속성을 하나만 표시 하는 넓은 테이블로 개체의 형식을 지정 합니다. **Property** 매개 변수를 사용 하 여 표시 되는 속성을 확인할 수 있습니다.

## 예제

### 예 1: 현재 디렉터리에 있는 파일의 형식 이름

이 명령은 화면 전체의 세 열에 현재 디렉터리의 파일 이름을 표시합니다.

```powershell
Get-ChildItem | Format-Wide -Column 3
```

Get-ChildItem cmdlet은 디렉터리의 각 파일을 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)가 파이프라인을 통해 파일 개체를에 전달 하 여 `Format-Wide` 출력 형식을 지정 합니다. **Column** 매개 변수는 열 수를 지정 합니다.

### 예제 2: 레지스트리 키의 형식 이름

이 명령은 HKEY_CURRENT_USER\Software\Microsoft 키에 레지스트리 키의 이름을 표시합니다.

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

Get-ChildItem cmdlet은 키를 나타내는 개체를 가져옵니다. 경로는 HKCU:, PowerShell 레지스트리 공급자에 의해 노출 되는 드라이브 중 하나인 키 경로로 지정 됩니다. 파이프라인 연산자 (|)가 파이프라인을 통해 레지스트리 키 개체를에 전달 하 여 `Format-Wide` 출력 형식을 지정 합니다. **Property** 매개 변수는 속성의 이름을 지정 하 고 **AutoSize** 매개 변수는 가독성을 위해 열을 조정 합니다.

### 예 3: 형식 오류 문제 해결

다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -AutoSize

데이터의 너비에 따라 열 크기 및 열 수를 조정합니다. 기본적으로 열 크기 및 수는 뷰에 따라 결정됩니다. **AutoSize** 및 **Column** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

### -열

표시에서 열의 개수를 지정합니다. **AutoSize** 및 **Column** 매개 변수는 동일한 명령에서 사용할 수 없습니다.

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

명령줄에 오류를 표시합니다. 이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Wide` .

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

컬렉션의 개체와 함께 컬렉션 개체의 형식을 지정합니다. 이 매개 변수는 ICollection(System.Collections) 인터페이스를 지원하는 개체의 형식을 지정할 수 있습니다. 기본값은 **Enumonly** 입니다.

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

이 cmdlet은 명령이 성공 하는 것을 방해 하는 제한을 무시 하므로 변경 내용이 보안을 손상 시 키 지 않습니다. 예를 들어 **Force** 는 읽기 전용 특성을 재정의하거나, 디렉터리를 만들어 파일 경로를 완성할 수 있지만 파일 사용 권한을 변경하지는 못합니다.

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

형식을 지정할 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

- 식 `<string>` 또는 `<script block>`
- FormatString `<string>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

파이프라인을 통해 오류를 보냅니다. 이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Wide` .

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

대체 테이블 형식 또는 뷰의 이름을 지정 합니다. 동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.

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

모든 개체를로 파이프 할 수 있습니다 `Format-Wide` .

## 출력

### Microsoft. PowerShell. Internal. Format

`Format-Wide` 테이블을 나타내는 형식 개체를 반환 합니다.

## 참고

의 기본 제공 별칭인를 참조할 수도 있습니다 `Format-Wide` `fw` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다. 를 사용 하 여 `Sort-Object` 개체를 그룹화 하기 전에 `Format-Custom` 를 사용 합니다.

**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식을 지정할 수 있습니다. PowerShell 디렉터리의 파일에 정의 된 보기를 사용 `*.format.PS1XML` 하거나 새 types.ps1xml 파일에서 고유한 뷰를 만들고 `Update-FormatData` cmdlet을 사용 하 여 powershell에 포함할 수 있습니다.

**View** 매개 변수의 대체 뷰에서는 테이블 형식을 사용 해야 합니다. 그렇지 않으면 명령이 실패 합니다. 대체 뷰가 목록이 면를 사용 `Format-List` 합니다. 대체 뷰가 목록이나 테이블이 아니면 Format-Custom을 사용합니다.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)
