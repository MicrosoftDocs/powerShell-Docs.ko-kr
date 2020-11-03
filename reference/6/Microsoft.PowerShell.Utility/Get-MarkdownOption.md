---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-6&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: df141d99080a0d893d72691f6032684097dfd966
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "93208960"
---
# <span data-ttu-id="9055d-101">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="9055d-101">Get-MarkdownOption</span></span>

## <span data-ttu-id="9055d-102">개요</span><span class="sxs-lookup"><span data-stu-id="9055d-102">SYNOPSIS</span></span>
<span data-ttu-id="9055d-103">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 현재 색과 스타일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9055d-103">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="9055d-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9055d-104">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="9055d-105">설명</span><span class="sxs-lookup"><span data-stu-id="9055d-105">DESCRIPTION</span></span>

<span data-ttu-id="9055d-106">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 현재 색과 스타일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9055d-106">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="9055d-107">이 cmdlet의 출력에 표시 되는 문자열에는 렌더링 되는 Markdown 텍스트의 색과 스타일을 변경 하는 데 사용 되는 ANSI 이스케이프 코드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9055d-107">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="9055d-108">Markdown에 대 한 자세한 내용은 [CommonMark](https://commonmark.org/) 웹 사이트를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9055d-108">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="9055d-109">예제</span><span class="sxs-lookup"><span data-stu-id="9055d-109">EXAMPLES</span></span>

### <span data-ttu-id="9055d-110">예제 1-현재 색 및 스타일 가져오기</span><span class="sxs-lookup"><span data-stu-id="9055d-110">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="9055d-111">출력에 표시 되는 문자열 값은 **Escape** `[char]0x1B` ANSI 이스케이프 시퀀스에 대 한 이스케이프 문자 () 뒤에 오는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="9055d-111">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="9055d-112">ANSI 이스케이프 코드 작업에 대 한 자세한 내용은 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9055d-112">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="9055d-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9055d-113">PARAMETERS</span></span>

### <span data-ttu-id="9055d-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9055d-114">CommonParameters</span></span>

<span data-ttu-id="9055d-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9055d-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9055d-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9055d-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9055d-117">입력</span><span class="sxs-lookup"><span data-stu-id="9055d-117">INPUTS</span></span>

### <span data-ttu-id="9055d-118">없음</span><span class="sxs-lookup"><span data-stu-id="9055d-118">None</span></span>

## <span data-ttu-id="9055d-119">출력</span><span class="sxs-lookup"><span data-stu-id="9055d-119">OUTPUTS</span></span>

### <span data-ttu-id="9055d-120">PSMarkdownOptionInfo입니다.</span><span class="sxs-lookup"><span data-stu-id="9055d-120">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="9055d-121">참고</span><span class="sxs-lookup"><span data-stu-id="9055d-121">NOTES</span></span>

## <span data-ttu-id="9055d-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9055d-122">RELATED LINKS</span></span>

[<span data-ttu-id="9055d-123">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="9055d-123">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="9055d-124">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="9055d-124">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="9055d-125">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="9055d-125">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="9055d-126">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="9055d-126">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="9055d-127">CommonMark</span><span class="sxs-lookup"><span data-stu-id="9055d-127">CommonMark</span></span>](https://commonmark.org/)
