---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-MarkdownOption
ms.openlocfilehash: b8353bf6eb9669676d72f533bffb25748e4e2827
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195223"
---
# <span data-ttu-id="f8d6d-102">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="f8d6d-102">Set-MarkdownOption</span></span>

## <span data-ttu-id="f8d6d-103">개요</span><span class="sxs-lookup"><span data-stu-id="f8d6d-103">SYNOPSIS</span></span>
<span data-ttu-id="f8d6d-104">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 색 및 스타일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-104">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="f8d6d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f8d6d-105">SYNTAX</span></span>

### <span data-ttu-id="f8d6d-106">IndividualSetting (기본값)</span><span class="sxs-lookup"><span data-stu-id="f8d6d-106">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="f8d6d-107">테마</span><span class="sxs-lookup"><span data-stu-id="f8d6d-107">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="f8d6d-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="f8d6d-108">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="f8d6d-109">설명</span><span class="sxs-lookup"><span data-stu-id="f8d6d-109">DESCRIPTION</span></span>

<span data-ttu-id="f8d6d-110">콘솔에서 Markdown 콘텐츠를 렌더링 하는 데 사용 되는 색 및 스타일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-110">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="f8d6d-111">이러한 스타일은 렌더링 되는 Markdown 텍스트의 색과 스타일을 변경 하는 ANSI 이스케이프 코드를 사용 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-111">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="f8d6d-112">Markdown에 대 한 자세한 내용은 [CommonMark](https://commonmark.org/) 웹 사이트를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-112">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="f8d6d-113">설정에 사용 되는 문자열 값은  `[char]0x1B` ANSI 이스케이프 시퀀스에 대 한 이스케이프 문자 () 뒤에 오는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-113">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="f8d6d-114">문자열에 **이스케이프** 문자를 포함 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-114">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="f8d6d-115">ANSI 이스케이프 코드 작업에 대 한 자세한 내용은 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-115">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="f8d6d-116">예제</span><span class="sxs-lookup"><span data-stu-id="f8d6d-116">EXAMPLES</span></span>

### <span data-ttu-id="f8d6d-117">예제 1-밝은 테마로 전환</span><span class="sxs-lookup"><span data-stu-id="f8d6d-117">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="f8d6d-118">이 예에서는 **Light** 테마를 선택 하 고 **PassThru** 매개 변수를 사용 하 여 새 구성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-118">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

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

### <span data-ttu-id="f8d6d-119">예제 2-색 및 스타일 설정 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="f8d6d-119">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="f8d6d-120">이 예제에서는 Markdown 헤더에 대 한 이스케이프 코드를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-120">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="f8d6d-121">헤더에 대 한 기본 구성은 다양 한 색의 밑줄로 표시 된 텍스트로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-121">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="f8d6d-122">이 변경 내용은 밑줄 스타일을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-122">This change removes the underline style.</span></span>

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

## <span data-ttu-id="f8d6d-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f8d6d-123">PARAMETERS</span></span>

### <span data-ttu-id="f8d6d-124">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f8d6d-124">-BoldForegroundColor</span></span>

<span data-ttu-id="f8d6d-125">굵은 글꼴 Markdown 텍스트를 렌더링 하기 위한 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-125">Sets the foreground color for rendering bold Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-126">-코드</span><span class="sxs-lookup"><span data-stu-id="f8d6d-126">-Code</span></span>

<span data-ttu-id="f8d6d-127">Markdown 텍스트에서 코드 블록 및 범위를 렌더링 하기 위한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-127">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-128">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="f8d6d-128">-Header1Color</span></span>

<span data-ttu-id="f8d6d-129">Markdown text의 렌더링 Header1 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-129">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-130">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="f8d6d-130">-Header2Color</span></span>

<span data-ttu-id="f8d6d-131">Markdown text의 렌더링 .Header2 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-131">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-132">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="f8d6d-132">-Header3Color</span></span>

<span data-ttu-id="f8d6d-133">Markdown text의 렌더링 Header3 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-133">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-134">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="f8d6d-134">-Header4Color</span></span>

<span data-ttu-id="f8d6d-135">Markdown text의 렌더링 Header4 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-135">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-136">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="f8d6d-136">-Header5Color</span></span>

<span data-ttu-id="f8d6d-137">Markdown text의 렌더링 Header5 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-137">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-138">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="f8d6d-138">-Header6Color</span></span>

<span data-ttu-id="f8d6d-139">Markdown text의 렌더링 Header6 블록에 대 한 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-139">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-140">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f8d6d-140">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="f8d6d-141">Markdown text에서 image 요소의 대체 텍스트를 렌더링 하기 위한 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-141">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f8d6d-142">-InputObject</span></span>

<span data-ttu-id="f8d6d-143">설정할 구성이 포함 된 **PSMarkdownOptionInfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-143">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

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

### <span data-ttu-id="f8d6d-144">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f8d6d-144">-ItalicsForegroundColor</span></span>

<span data-ttu-id="f8d6d-145">Markdown 텍스트에서 기울임꼴 렌더링에 사용할 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-145">Sets the foreground color for rendering the italics in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-146">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f8d6d-146">-LinkForegroundColor</span></span>

<span data-ttu-id="f8d6d-147">Markdown 텍스트에서 하이퍼링크를 렌더링 하기 위한 전경색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-147">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

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

### <span data-ttu-id="f8d6d-148">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f8d6d-148">-PassThru</span></span>

<span data-ttu-id="f8d6d-149">Cmdlet이 새 구성을 포함 하는 **PSMarkdownOptionInfo** 개체를 출력 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-149">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="f8d6d-150">-테마</span><span class="sxs-lookup"><span data-stu-id="f8d6d-150">-Theme</span></span>

<span data-ttu-id="f8d6d-151">미리 정의 된 색 설정이 포함 된 테마를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-151">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="f8d6d-152">가능한 값은 **어두움** 및 **Light** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-152">The possible values are **Dark** and **Light**.</span></span>

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

### <span data-ttu-id="f8d6d-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8d6d-153">CommonParameters</span></span>

<span data-ttu-id="f8d6d-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f8d6d-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f8d6d-156">입력</span><span class="sxs-lookup"><span data-stu-id="f8d6d-156">INPUTS</span></span>

### <span data-ttu-id="f8d6d-157">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="f8d6d-157">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="f8d6d-158">출력</span><span class="sxs-lookup"><span data-stu-id="f8d6d-158">OUTPUTS</span></span>

### <span data-ttu-id="f8d6d-159">PSMarkdownOptionInfo입니다.</span><span class="sxs-lookup"><span data-stu-id="f8d6d-159">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="f8d6d-160">참고</span><span class="sxs-lookup"><span data-stu-id="f8d6d-160">NOTES</span></span>

<span data-ttu-id="f8d6d-161">색 및 스타일을 정의 하는 데 사용 되는 문자열 값은 정규식과 일치 해야 합니다 `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="f8d6d-161">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="f8d6d-162">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f8d6d-162">RELATED LINKS</span></span>

[<span data-ttu-id="f8d6d-163">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="f8d6d-163">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="f8d6d-164">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="f8d6d-164">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="f8d6d-165">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="f8d6d-165">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="f8d6d-166">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="f8d6d-166">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="f8d6d-167">CommonMark</span><span class="sxs-lookup"><span data-stu-id="f8d6d-167">CommonMark</span></span>](https://commonmark.org/)

