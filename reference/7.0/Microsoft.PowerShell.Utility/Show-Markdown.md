---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: bb73853c8432bcd4fcc900ee1d6fc620ed883ebb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210161"
---
# <span data-ttu-id="b2a61-103">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="b2a61-103">Show-Markdown</span></span>

## <span data-ttu-id="b2a61-104">개요</span><span class="sxs-lookup"><span data-stu-id="b2a61-104">SYNOPSIS</span></span>
<span data-ttu-id="b2a61-105">HTML을 사용 하는 브라우저에서 VT100 이스케이프 시퀀스를 사용 하 여 친숙 한 방법으로 콘솔에 Markdown 파일 또는 문자열을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-105">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="b2a61-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2a61-106">SYNTAX</span></span>

### <span data-ttu-id="b2a61-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="b2a61-107">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="b2a61-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="b2a61-108">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="b2a61-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b2a61-109">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="b2a61-110">설명</span><span class="sxs-lookup"><span data-stu-id="b2a61-110">DESCRIPTION</span></span>

<span data-ttu-id="b2a61-111">`Show-Markdown`이 cmdlet은 터미널 또는 브라우저에서 Markdown을 사람이 읽을 수 있는 형식으로 렌더링 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-111">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="b2a61-112">`Show-Markdown` 는 터미널에서 렌더링 하는 VT100 이스케이프 시퀀스를 포함 하는 문자열을 반환할 수 있습니다 (VT100 이스케이프 시퀀스를 지 원하는 경우).</span><span class="sxs-lookup"><span data-stu-id="b2a61-112">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="b2a61-113">이는 주로 터미널의 Markdown 파일을 보는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-113">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="b2a61-114">`ConvertFrom-Markdown` **AsVT100EncodedString** 매개 변수를 지정 하 여를 통해이 문자열을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-114">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="b2a61-115">`Show-Markdown` 또한에는 브라우저를 열고 렌더링 된 버전의 Markdown를 표시 하는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-115">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="b2a61-116">HTML로 전환 하 고 기본 브라우저에서 HTML 파일을 열어 Markdown을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-116">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="b2a61-117">를 `Show-Markdown` 사용 하 여가 터미널에서 Markdown를 렌더링 하는 방식을 변경할 수 있습니다 `Set-MarkdownOption` .</span><span class="sxs-lookup"><span data-stu-id="b2a61-117">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="b2a61-118">이 cmdlet은 PowerShell 6.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-118">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="b2a61-119">예제</span><span class="sxs-lookup"><span data-stu-id="b2a61-119">EXAMPLES</span></span>

### <span data-ttu-id="b2a61-120">예제 1: 경로를 지정 하는 간단한 예제</span><span class="sxs-lookup"><span data-stu-id="b2a61-120">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="b2a61-121">예제 2: 문자열을 지정 하는 간단한 예제</span><span class="sxs-lookup"><span data-stu-id="b2a61-121">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="b2a61-122">예제 2: 브라우저에서 Markdown 열기</span><span class="sxs-lookup"><span data-stu-id="b2a61-122">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="b2a61-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2a61-123">PARAMETERS</span></span>

### <span data-ttu-id="b2a61-124">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b2a61-124">-InputObject</span></span>

<span data-ttu-id="b2a61-125">터미널에 표시 되는 Markdown 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-125">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="b2a61-126">지원 되는 형식을 전달 하지 않으면에서 오류를 `Show-Markdown` 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-126">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

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

### <span data-ttu-id="b2a61-127">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b2a61-127">-LiteralPath</span></span>

<span data-ttu-id="b2a61-128">Markdown 파일에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-128">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="b2a61-129">Path 매개 변수와 달리 LiteralPath 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-129">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="b2a61-130">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-130">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b2a61-131">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="b2a61-131">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b2a61-132">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-132">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b2a61-133">-Path</span><span class="sxs-lookup"><span data-stu-id="b2a61-133">-Path</span></span>

<span data-ttu-id="b2a61-134">렌더링할 Markdown 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-134">Specifies the path to a Markdown file to be rendered.</span></span>

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

### <span data-ttu-id="b2a61-135">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="b2a61-135">-UseBrowser</span></span>

<span data-ttu-id="b2a61-136">Markdown 입력을 HTML로 컴파일하고 기본 브라우저에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2a61-136">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

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

### <span data-ttu-id="b2a61-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2a61-137">CommonParameters</span></span>

<span data-ttu-id="b2a61-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2a61-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2a61-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2a61-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2a61-140">입력</span><span class="sxs-lookup"><span data-stu-id="b2a61-140">INPUTS</span></span>

### <span data-ttu-id="b2a61-141">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="b2a61-141">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="b2a61-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b2a61-142">System.String[]</span></span>

## <span data-ttu-id="b2a61-143">출력</span><span class="sxs-lookup"><span data-stu-id="b2a61-143">OUTPUTS</span></span>

### <span data-ttu-id="b2a61-144">System.String</span><span class="sxs-lookup"><span data-stu-id="b2a61-144">System.String</span></span>

## <span data-ttu-id="b2a61-145">참고</span><span class="sxs-lookup"><span data-stu-id="b2a61-145">NOTES</span></span>

## <span data-ttu-id="b2a61-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b2a61-146">RELATED LINKS</span></span>

[<span data-ttu-id="b2a61-147">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="b2a61-147">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)
