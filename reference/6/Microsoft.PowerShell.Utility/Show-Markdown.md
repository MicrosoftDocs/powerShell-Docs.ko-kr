---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: 2d88b24519f472f0c167dc5138450ab542a8b7cf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216218"
---
# Show-Markdown

## 개요
HTML을 사용 하는 브라우저에서 VT100 이스케이프 시퀀스를 사용 하 여 친숙 한 방법으로 콘솔에 Markdown 파일 또는 문자열을 표시 합니다.

## SYNTAX

### Path (기본값)

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### InputObject

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### LiteralPath

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## 설명

`Show-Markdown`이 cmdlet은 터미널 또는 브라우저에서 Markdown을 사람이 읽을 수 있는 형식으로 렌더링 하는 데 사용 됩니다.

`Show-Markdown` 는 터미널에서 렌더링 하는 VT100 이스케이프 시퀀스를 포함 하는 문자열을 반환할 수 있습니다 (VT100 이스케이프 시퀀스를 지 원하는 경우). 이는 주로 터미널의 Markdown 파일을 보는 데 사용 됩니다. `ConvertFrom-Markdown` **AsVT100EncodedString** 매개 변수를 지정 하 여를 통해이 문자열을 가져올 수도 있습니다.

`Show-Markdown` 또한에는 브라우저를 열고 렌더링 된 버전의 Markdown를 표시 하는 기능이 있습니다. HTML로 전환 하 고 기본 브라우저에서 HTML 파일을 열어 Markdown을 렌더링 합니다.

를 `Show-Markdown` 사용 하 여가 터미널에서 Markdown를 렌더링 하는 방식을 변경할 수 있습니다 `Set-MarkdownOption` .

이 cmdlet은 PowerShell 6.1에서 도입 되었습니다.

## 예제

### 예제 1: 경로를 지정 하는 간단한 예제

```powershell
Show-Markdown -Path ./README.md
```

### 예제 2: 문자열을 지정 하는 간단한 예제

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### 예제 2: 브라우저에서 Markdown 열기

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## PARAMETERS

### -InputObject

터미널에 표시 되는 Markdown 문자열입니다. 지원 되는 형식을 전달 하지 않으면에서 오류를 `Show-Markdown` 내보냅니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Markdown 파일에 대 한 경로를 지정 합니다. Path 매개 변수와 달리 LiteralPath 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

렌더링할 Markdown 파일의 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -UseBrowser

Markdown 입력을 HTML로 컴파일하고 기본 브라우저에서 엽니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

### System.String[]

## 출력

### System.String

## 참고

## 관련 링크

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)
