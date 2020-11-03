---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e7e70637afcf53f84c719b489575f5267f9048b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211817"
---
# <span data-ttu-id="c3777-101">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="c3777-101">Set-MarkdownOption</span></span>

## <span data-ttu-id="c3777-102">개요</span><span class="sxs-lookup"><span data-stu-id="c3777-102">SYNOPSIS</span></span>
<span data-ttu-id="c3777-103">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 색 및 스타일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-103">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="c3777-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3777-104">SYNTAX</span></span>

### <span data-ttu-id="c3777-105">IndividualSetting (기본값)</span><span class="sxs-lookup"><span data-stu-id="c3777-105">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="c3777-106">테마</span><span class="sxs-lookup"><span data-stu-id="c3777-106">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="c3777-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="c3777-107">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="c3777-108">설명</span><span class="sxs-lookup"><span data-stu-id="c3777-108">DESCRIPTION</span></span>

<span data-ttu-id="c3777-109">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 색 및 스타일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-109">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="c3777-110">이러한 스타일은 렌더링 되는 Markdown 텍스트의 색과 스타일을 변경 하는 ANSI 이스케이프 코드를 사용 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-110">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="c3777-111">Markdown에 대 한 자세한 내용은 [CommonMark](https://commonmark.org/) 웹 사이트를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3777-111">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="c3777-112">설정에 사용 되는 문자열 값은 **Escape** `[char]0x1B` ANSI 이스케이프 시퀀스에 대 한 이스케이프 문자 () 뒤에 오는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-112">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="c3777-113">문자열에 **이스케이프** 문자를 포함 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c3777-113">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="c3777-114">ANSI 이스케이프 코드 작업에 대 한 자세한 내용은 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3777-114">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="c3777-115">예제</span><span class="sxs-lookup"><span data-stu-id="c3777-115">EXAMPLES</span></span>

### <span data-ttu-id="c3777-116">예제 1-밝은 테마로 전환</span><span class="sxs-lookup"><span data-stu-id="c3777-116">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="c3777-117">이 예에서는 **Light** 테마를 선택 하 고 **PassThru** 매개 변수를 사용 하 여 새 구성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-117">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### <span data-ttu-id="c3777-118">예제 2-색 및 스타일 설정 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="c3777-118">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="c3777-119">이 예제에서는 Markdown 헤더에 대 한 이스케이프 코드를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-119">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="c3777-120">헤더에 대 한 기본 구성은 다양 한 색의 밑줄로 표시 된 텍스트로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-120">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="c3777-121">이 변경 내용은 밑줄 스타일을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-121">This change removes the underline style.</span></span>

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## <span data-ttu-id="c3777-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3777-122">PARAMETERS</span></span>

### <span data-ttu-id="c3777-123">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c3777-123">-BoldForegroundColor</span></span>

<span data-ttu-id="c3777-124">굵은 글꼴 Markdown 텍스트를 렌더링 하기 위한 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-124">Sets the foreground color for rendering bold Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-125">-코드</span><span class="sxs-lookup"><span data-stu-id="c3777-125">-Code</span></span>

<span data-ttu-id="c3777-126">Markdown 텍스트에서 코드 블록 및 범위를 렌더링 하기 위한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-126">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-127">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="c3777-127">-Header1Color</span></span>

<span data-ttu-id="c3777-128">Markdown text의 렌더링 Header1 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-128">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-129">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="c3777-129">-Header2Color</span></span>

<span data-ttu-id="c3777-130">Markdown text의 렌더링 .Header2 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-130">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-131">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="c3777-131">-Header3Color</span></span>

<span data-ttu-id="c3777-132">Markdown text의 렌더링 Header3 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-132">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-133">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="c3777-133">-Header4Color</span></span>

<span data-ttu-id="c3777-134">Markdown text의 렌더링 Header4 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-134">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-135">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="c3777-135">-Header5Color</span></span>

<span data-ttu-id="c3777-136">Markdown text의 렌더링 Header5 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-136">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-137">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="c3777-137">-Header6Color</span></span>

<span data-ttu-id="c3777-138">Markdown text의 렌더링 Header6 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-138">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-139">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c3777-139">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="c3777-140">Markdown text에서 image 요소의 대체 텍스트를 렌더링 하기 위한 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-140">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c3777-141">-InputObject</span></span>

<span data-ttu-id="c3777-142">설정할 구성이 포함 된 **PSMarkdownOptionInfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-142">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-143">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c3777-143">-ItalicsForegroundColor</span></span>

<span data-ttu-id="c3777-144">Markdown 텍스트에서 기울임꼴 렌더링에 사용할 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-144">Sets the foreground color for rendering the italics in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-145">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c3777-145">-LinkForegroundColor</span></span>

<span data-ttu-id="c3777-146">Markdown 텍스트에서 하이퍼링크를 렌더링 하기 위한 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-146">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="c3777-147">-PassThru</span></span>

<span data-ttu-id="c3777-148">Cmdlet이 새 구성을 포함 하는 **PSMarkdownOptionInfo** 개체를 출력 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-148">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="c3777-149">-테마</span><span class="sxs-lookup"><span data-stu-id="c3777-149">-Theme</span></span>

<span data-ttu-id="c3777-150">미리 정의 된 색 설정이 포함 된 테마를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-150">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="c3777-151">가능한 값은 **어두움** 및 **Light** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-151">The possible values are **Dark** and **Light** .</span></span>

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3777-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3777-152">CommonParameters</span></span>

<span data-ttu-id="c3777-153">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3777-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3777-154">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3777-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3777-155">입력</span><span class="sxs-lookup"><span data-stu-id="c3777-155">INPUTS</span></span>

### <span data-ttu-id="c3777-156">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="c3777-156">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="c3777-157">출력</span><span class="sxs-lookup"><span data-stu-id="c3777-157">OUTPUTS</span></span>

### <span data-ttu-id="c3777-158">PSMarkdownOptionInfo입니다.</span><span class="sxs-lookup"><span data-stu-id="c3777-158">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="c3777-159">참고</span><span class="sxs-lookup"><span data-stu-id="c3777-159">NOTES</span></span>

<span data-ttu-id="c3777-160">색 및 스타일을 정의 하는 데 사용 되는 문자열 값은 정규식과 일치 해야 합니다 `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="c3777-160">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="c3777-161">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c3777-161">RELATED LINKS</span></span>

[<span data-ttu-id="c3777-162">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="c3777-162">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="c3777-163">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="c3777-163">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="c3777-164">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="c3777-164">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="c3777-165">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="c3777-165">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="c3777-166">CommonMark</span><span class="sxs-lookup"><span data-stu-id="c3777-166">CommonMark</span></span>](https://commonmark.org/)

