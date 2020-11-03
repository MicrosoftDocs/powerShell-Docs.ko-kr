---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 209e5cf9ab5809767b4135817640ffe7c2d69175
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210498"
---
# Update-FormatData

## 개요
현재 세션에 있는 형식 지정 데이터를 업데이트합니다.

## SYNTAX

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

Cmdlet은 형식 지정 `Update-FormatData` 파일의 형식 지정 데이터를 현재 세션으로 다시 로드 합니다. 이 cmdlet을 사용 하면 PowerShell을 다시 시작 하지 않고도 형식 지정 데이터를 업데이트할 수 있습니다.

매개 변수가 없으면 `Update-FormatData` 이전에 로드 한 형식 지정 파일을 다시 로드 합니다.
의 매개 변수를 사용 `Update-FormatData` 하 여 새 형식 지정 파일을 세션에 추가할 수 있습니다.

서식 파일은 파일 이름 확장명을 사용 하는 XML 형식의 텍스트 파일 `format.ps1xml` 입니다. 이 파일의 형식 지정 데이터는 세션에서 Microsoft .NET Framework 개체의 표시를 정의합니다.

PowerShell이 시작 되 면 PowerShell 소스 코드에서 형식 데이터를 로드 합니다. 그러나 사용자 지정 format.ps1xml 파일을 만들어 현재 세션의 형식을 업데이트할 수 있습니다. `Update-FormatData`PowerShell을 다시 시작 하지 않고를 사용 하 여 형식 지정 데이터를 현재 세션으로 다시 로드할 수 있습니다. 이 방법은 형식 지정 파일을 추가하거나 변경했지만 세션을 중단하지 않으려는 경우에 유용합니다.

PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.

## 예제

### 예제 1: 이전에 로드 한 서식 파일 다시 로드

```powershell
Update-FormatData
```

이 명령은 이전에 로드한 형식 지정 파일을 다시 로드합니다.

### 예 2: 형식 지정 파일 및 추적 및 로그 서식 파일 다시 로드

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

이 명령은 두 개의 새 파일 Trace.format.ps1xml 및 Log.format.ps1xml을 비롯한 형식 지정 파일을 세션으로 다시 로드합니다.

이 명령은 **Appendpath** 매개 변수를 사용 하므로 기본 제공 파일의 형식 지정 데이터 이후에 새 파일의 형식 지정 데이터가 로드 됩니다.

새 파일에 기본 제공 파일에서 참조 되지 않는 개체에 대 한 형식 지정 데이터가 포함 되어 있으므로 **Appendpath** 매개 변수를 사용 합니다.

### 예제 3: 서식 파일 편집 및 다시 로드

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

이 예제에서는 형식 지정 파일을 편집한 후 다시 로드하는 방법을 보여 줍니다.

첫 번째 명령은 NewFiles.format.ps1xml 파일을 세션에 추가합니다. **PrependPath** 매개 변수를 사용 합니다 .이 파일에는 기본 제공 파일에서 참조 되는 개체에 대 한 형식 지정 데이터가 포함 되어 있기 때문입니다.

NewFiles.format.ps1xml 파일을 추가 하 고 이러한 세션에서 테스트 한 후에는 작성자가 파일을 편집 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Update-FormatData` 형식 지정 파일을 다시 로드 합니다. NewFiles.format.ps1xml 파일이 이전에 로드 되었으므로는 `Update-FormatData` 매개 변수를 사용 하지 않고 자동으로 다시 로드 합니다.

## PARAMETERS

### -AppendPath

이 cmdlet이 세션에 추가 하는 형식 지정 파일을 지정 합니다. 파일은 PowerShell에서 기본 제공 형식 지정 파일을 로드 한 후에 로드 됩니다.

.NET 개체의 형식을 지정 하는 경우 PowerShell은 각 .NET 유형에 대해 찾은 첫 번째 형식 지정 정의를 사용 합니다. **Appendpath** 매개 변수를 사용 하는 경우 PowerShell은 사용자가 추가 하는 형식 지정 데이터를 찾기 전에 기본 제공 파일에서 데이터를 검색 합니다.

이 매개 변수를 사용하면 기본 형식 지정 파일에서 참조되지 않는 .NET 개체의 형식을 지정하는 파일을 추가할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PrependPath

이 cmdlet이 세션에 추가 하는 형식 지정 파일을 지정 합니다. 파일은 PowerShell에서 기본 제공 형식 지정 파일을 로드 하기 전에 로드 됩니다.

.NET 개체의 형식을 지정 하는 경우 PowerShell은 각 .NET 유형에 대해 찾은 첫 번째 형식 지정 정의를 사용 합니다. **PrependPath** 매개 변수를 사용 하는 경우 PowerShell은 기본 제공 파일의 형식 지정 데이터를 발생 하기 전에 추가 하는 파일에서 데이터를 검색 합니다.

이 매개 변수를 사용하면 기본 형식 지정 파일에서도 참조되는 .NET 개체의 형식을 지정하는 파일을 추가할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

추가 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Update-FormatData` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

- `Update-FormatData` 는 모듈에서 가져온 세션의 명령에 대 한 형식 지정 데이터도 업데이트 합니다. 모듈에 대 한 형식 지정 파일이 변경 되 면 `Update-FormatData` 명령을 실행 하 여 가져온 명령에 대 한 형식 지정 데이터를 업데이트할 수 있습니다. 모듈을 다시 가져올 필요는 없습니다.

## 관련 링크

[Get-FormatData](Get-FormatData.md)

[Export-FormatData](Export-FormatData.md)
