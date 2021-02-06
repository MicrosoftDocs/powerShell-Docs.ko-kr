---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d42b108d469ed8989628a6c0b4214af4afc0db00
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605480"
---
# Export-FormatData

## 개요
현재 세션의 형식 지정 데이터를 형식 지정 파일에 저장합니다.

## SYNTAX

### ByPath (기본값)

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### ByLiteralPath

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## 설명

`Export-FormatData`Cmdlet은 현재 세션의 형식 지정 개체에서 PowerShell 형식 지정 파일 (format.ps1xml)을 만듭니다. 이 클래스는를 반환 하 고 XML 형식의 파일로 저장 하는 **Extendedtypedefinition** 개체를 사용 `Get-FormatData` 합니다.

PowerShell에서는 서식 파일 (format.ps1xml)의 데이터를 사용 하 여 세션에서 Microsoft .NET Framework 개체의 기본 표시를 생성 합니다. 사용자는 형식 지정 파일을 보고 편집할 수 있으며 Update-FormatData cmdlet을 사용하여 세션에 형식 지정 데이터를 추가할 수 있습니다.

PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.

## 예제

### 예제 1: 세션 형식 데이터 내보내기

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

이 명령은 세션의 모든 형식 데이터를 AllFormat.ps1xml 파일로 내보냅니다.

이 명령은 cmdlet을 사용 하 여 `Get-FormatData` 세션의 형식 데이터를 가져옵니다. `*` **TypeName** 매개 변수의 값 (모두)은 cmdlet에 게 세션의 모든 데이터를 가져오도록 지시 합니다.

이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 명령에서 형식 데이터를 `Get-FormatData` cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 형식 데이터를 AllFormat.ps1 파일로 내보냅니다.

이 `Export-FormatData` 명령은 **IncludeScriptBlock** 매개 변수를 사용 하 여 파일의 형식 데이터에 스크립트 블록을 포함 합니다.

### 예 2: 형식에 대 한 형식 데이터 내보내기

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

이러한 명령은 **Helpinfoshort** 유형의 형식 데이터를 Help.format.ps1xml 파일로 내보냅니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` **Helpinfoshort** 유형의 형식 데이터를 가져온 다음 변수에 저장 합니다 `$F` .

두 번째 명령은 cmdlet의 **InputObject** 매개 변수 `Export-FormatData` 를 사용 하 여 변수에 저장 된 형식 데이터를 입력 합니다 `$F` . 또한 **IncludeScriptBlock** 매개 변수를 사용 하 여 스크립트 블록을 출력에 포함 합니다.

### 예제 3: 스크립트 블록 없이 형식 데이터 내보내기

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

이 예에서는 명령에서 **IncludeScriptBlock** 매개 변수를 생략 하는 경우의 결과를 보여 줍니다 `Export-FormatData` .

첫 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` Get-Process cmdlet이 반환 하는 **system.object** 개체의 형식 데이터를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 형식 지정 데이터를 cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 현재 디렉터리의 Process.format.ps1xml 파일로 내보냅니다.

이 경우 `Export-FormatData` 명령은 **IncludeScriptBlock** 매개 변수를 사용 하지 않습니다.

두 번째 명령은 cmdlet을 사용 하 여 `Update-FormatData` Process.format.ps1xml 파일을 현재 세션에 추가 합니다. 이 명령은 **PrependPath** 매개 변수를 사용 하 여 Process.format.ps1xml 파일의 프로세스 개체에 대 한 형식 지정 데이터가 프로세스 개체에 대 한 표준 형식 지정 데이터 보다 먼저 검색 되도록 합니다.

세 번째 명령은 이 변경 사항의 효과를 보여 줍니다. 이 명령은 cmdlet을 사용 하 여 `Get-Process` 이름이 P로 시작 하는 프로세스를 가져옵니다. 출력은 스크립트 블록을 사용 하 여 계산 된 속성 값이 표시 되지 않는 것을 보여 줍니다.

## PARAMETERS

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### -IncludeScriptBlock

형식 데이터의 스크립트 블록을 내보낼지 여부를 나타냅니다.

스크립트 블록에는 코드가 포함되어 있어 악의적으로 사용될 수 있으므로 기본적으로 내보내지 않습니다.

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

### -InputObject

내보낼 형식 데이터 개체를 지정합니다. 개체를 포함 하는 변수를 입력 하거나 개체를 가져오는 명령 (예: 명령)을 입력 합니다 `Get-FormatData` . 에서로 개체를 파이프 할 수도 `Get-FormatData` 있습니다 `Export-FormatData` .

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

출력 파일의 위치를 지정합니다. **Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Cmdlet이 기존 파일을 덮어쓰지 않음을 나타냅니다. 기본적으로는 `Export-FormatData` 파일에 읽기 전용 특성이 있는 경우를 제외 하 고는 경고 없이 파일을 덮어씁니다.

읽기 전용 `Export-FormatData` 파일을 덮어쓰도록 지시 하려면 **Force** 매개 변수를 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

출력 파일의 위치를 지정합니다.
파일 이름 확장명이 format.ps1xml인 파일 이름과 경로(선택 사항)를 입력합니다.
경로를 생략 하면에서 `Export-FormatData` 현재 디렉터리에 파일을 만듭니다.

. Types.ps1xml 이외의 파일 이름 확장명을 사용 하는 경우 cmdlet은 `Update-FormatData` 파일을 인식 하지 못합니다.

기존 파일을 지정 하는 경우 `Export-FormatData` 파일에 읽기 전용 특성이 없으면에서 경고 없이 파일을 덮어씁니다. 읽기 전용 파일을 덮어쓰려면 **Force** 매개 변수를 사용 합니다. 파일을 덮어쓰지 않도록 하려면 **NoClobber** 매개 변수를 사용 합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. ExtendedTypeDefinition

**Extendedtypedefinition** 개체를에서로 파이프 할 수 있습니다 `Get-FormatData` `Export-FormatData` .

## 출력

### 없음

`Export-FormatData` 는 개체를 반환 하지 않습니다.
파일을 생성하여 지정된 경로에 저장합니다.

## 참고

- 내보낸 형식 지정 파일을 포함하여 모든 형식 지정 파일을 사용하려면 세션에 대한 실행 정책에서 스크립트와 구성 파일의 실행을 허용해야 합니다. 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)를 참조하세요.

## 관련 링크

[Get-FormatData](Get-FormatData.md)

[Update-FormatData](Update-FormatData.md)
