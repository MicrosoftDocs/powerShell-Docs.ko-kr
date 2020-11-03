---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: 52c0a94304156a7c1cf89bbc5ae98a0668789bd2
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2020
ms.locfileid: "93208968"
---
# Get-MarkdownOption

## 개요
콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 현재 색과 스타일을 반환 합니다.

## SYNTAX

```
Get-MarkdownOption [<CommonParameters>]
```

## 설명

콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 현재 색과 스타일을 반환 합니다. 이 cmdlet의 출력에 표시 되는 문자열에는 렌더링 되는 Markdown 텍스트의 색과 스타일을 변경 하는 데 사용 되는 ANSI 이스케이프 코드가 포함 됩니다.

Markdown에 대 한 자세한 내용은 [CommonMark](https://commonmark.org/) 웹 사이트를 참조 하세요.

## 예제

### 예제 1-현재 색 및 스타일 가져오기

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> 출력에 표시 되는 문자열 값은 **Escape** `[char]0x1B` ANSI 이스케이프 시퀀스에 대 한 이스케이프 문자 () 뒤에 오는 문자입니다. ANSI 이스케이프 코드 작업에 대 한 자세한 내용은 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)를 참조 하세요.

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### PSMarkdownOptionInfo입니다.

## 참고

## 관련 링크

[Set-MarkdownOption](Set-MarkdownOption.md)

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)

[Show-Markdown](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)

