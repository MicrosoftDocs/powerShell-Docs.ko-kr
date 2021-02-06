---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: c694e73e69c1e51ecf88f445684923ef5f19113f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601453"
---
# ConvertFrom-Markdown

## 개요
문자열 또는 파일의 내용을 **Markdowninfo** 개체로 변환 합니다.

## SYNTAX

### PathParamSet (기본값)

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### LiteralParamSet

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### InputObjParamSet

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## 설명

이 cmdlet은 지정 된 콘텐츠를 **Markdowninfo** 로 변환 합니다. **Path** 매개 변수에 대 한 파일 경로가 지정 된 경우 파일의 내용이 변환 됩니다. Output 개체에는 다음과 같은 세 가지 속성이 있습니다.

- **Token** 속성에는 변환 된 개체의 AST (추상 구문 트리)가 있습니다.
- **Html** 속성이 지정 된 입력을 html로 변환 합니다.
- **AsVT100EncodedString** 매개 변수가 지정 된 경우 **VT100EncodedString** 속성에는 ANSI (VT100) 이스케이프 시퀀스가 있는 변환 된 문자열이 있습니다.

이 cmdlet은 PowerShell 6.1에서 도입 되었습니다.

## 예제

### 예제 1: Markdown 콘텐츠를 포함 하는 파일을 HTML로 변환

```powershell
ConvertFrom-Markdown -Path .\README.md
```

**Markdowninfo** 개체가 반환 됩니다. **Tokens** 속성에는 파일의 변환 된 내용이 포함 된 AST가 있습니다 `README.md` . **Html** 속성에는 파일의 html 변환 내용이 포함 되어 `README.md` 있습니다.

### 예제 2: Markdown 콘텐츠를 포함 하는 파일을 VT100 인코딩된 문자열로 변환

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

**Markdowninfo** 개체가 반환 됩니다. **Tokens** 속성에는 파일의 변환 된 내용이 포함 된 AST가 있습니다 `README.md` . **VT100EncodedString** 속성은 파일의 VT100 인코딩된 문자열 변환 된 콘텐츠를 포함 합니다 `README.md` .

### 예제 3: Markdown 콘텐츠를 포함 하는 입력 개체를 VT100 인코딩된 문자열로 변환

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

**Markdowninfo** 개체가 반환 됩니다. 에서 **FileInfo** 개체는 `Get-Item` VT100 인코딩된 문자열로 변환 됩니다. **Tokens** 속성에는 파일의 변환 된 내용이 포함 된 AST가 있습니다 `README.md` . **VT100EncodedString** 속성은 파일의 VT100 인코딩된 문자열 변환 된 콘텐츠를 포함 합니다 `README.md` .

### 예제 4: Markdown 콘텐츠를 포함 하는 문자열을 VT100 인코딩된 문자열로 변환

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

**Markdowninfo** 개체가 반환 됩니다. 지정 된 문자열은 `**Bold text**` VT100 인코딩 문자열로 변환 되 고 **VT100EncodedString** 속성에서 사용할 수 있습니다.

## PARAMETERS

### -AsVT100EncodedString

출력을 VT100 이스케이프 코드가 포함 된 문자열로 인코딩해야 하는지 여부를 지정 합니다.

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

변환할 개체를 지정합니다. **System.string** 형식의 개체가 지정 되 면 문자열이 변환 됩니다. **System.object** 형식의 개체가 지정 되 면 개체에서 지정 된 파일의 내용이 변환 됩니다. 다른 형식의 개체는 오류가 발생 합니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

변환할 파일의 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

변환할 파일의 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

## 출력

### Microsoft. PowerShell. MarkdownRender. Markdownrender

## 참고

## 관련 링크

[Markdown 파서](https://github.com/lunet-io/markdig)

[ANSI 이스케이프 코드](https://wikipedia.org/wiki/ANSI_escape_code)

