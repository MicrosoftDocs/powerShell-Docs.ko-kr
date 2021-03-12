---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: 4fac43c411fd91575c7169baca3e2ea86bb64e18
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196315"
---
# <span data-ttu-id="c41c2-102">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="c41c2-102">Get-MarkdownOption</span></span>

## <span data-ttu-id="c41c2-103">개요</span><span class="sxs-lookup"><span data-stu-id="c41c2-103">SYNOPSIS</span></span>
<span data-ttu-id="c41c2-104">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 현재 색과 스타일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c2-104">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="c41c2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c41c2-105">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="c41c2-106">설명</span><span class="sxs-lookup"><span data-stu-id="c41c2-106">DESCRIPTION</span></span>

<span data-ttu-id="c41c2-107">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 현재 색과 스타일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c2-107">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="c41c2-108">이 cmdlet의 출력에 표시 되는 문자열에는 렌더링 되는 Markdown 텍스트의 색과 스타일을 변경 하는 데 사용 되는 ANSI 이스케이프 코드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c41c2-108">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="c41c2-109">Markdown에 대 한 자세한 내용은 [CommonMark](https://commonmark.org/) 웹 사이트를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c41c2-109">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="c41c2-110">예제</span><span class="sxs-lookup"><span data-stu-id="c41c2-110">EXAMPLES</span></span>

### <span data-ttu-id="c41c2-111">예제 1-현재 색 및 스타일 가져오기</span><span class="sxs-lookup"><span data-stu-id="c41c2-111">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="c41c2-112">출력에 표시 되는 문자열 값은  `[char]0x1B` ANSI 이스케이프 시퀀스에 대 한 이스케이프 문자 () 뒤에 오는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="c41c2-112">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="c41c2-113">ANSI 이스케이프 코드 작업에 대 한 자세한 내용은 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c41c2-113">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="c41c2-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c41c2-114">PARAMETERS</span></span>

### <span data-ttu-id="c41c2-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c41c2-115">CommonParameters</span></span>

<span data-ttu-id="c41c2-116">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c41c2-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c41c2-117">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c41c2-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c41c2-118">입력</span><span class="sxs-lookup"><span data-stu-id="c41c2-118">INPUTS</span></span>

### <span data-ttu-id="c41c2-119">None</span><span class="sxs-lookup"><span data-stu-id="c41c2-119">None</span></span>

## <span data-ttu-id="c41c2-120">출력</span><span class="sxs-lookup"><span data-stu-id="c41c2-120">OUTPUTS</span></span>

### <span data-ttu-id="c41c2-121">PSMarkdownOptionInfo입니다.</span><span class="sxs-lookup"><span data-stu-id="c41c2-121">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="c41c2-122">참고</span><span class="sxs-lookup"><span data-stu-id="c41c2-122">NOTES</span></span>

## <span data-ttu-id="c41c2-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c41c2-123">RELATED LINKS</span></span>

[<span data-ttu-id="c41c2-124">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="c41c2-124">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="c41c2-125">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="c41c2-125">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="c41c2-126">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="c41c2-126">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="c41c2-127">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="c41c2-127">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="c41c2-128">CommonMark</span><span class="sxs-lookup"><span data-stu-id="c41c2-128">CommonMark</span></span>](https://commonmark.org/)

