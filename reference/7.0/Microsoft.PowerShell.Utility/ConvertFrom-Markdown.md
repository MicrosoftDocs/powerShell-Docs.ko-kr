---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell, cmdlet, markdown
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: 6f1ccedbd8443e1259b5695d1848979336727def
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210922"
---
# <span data-ttu-id="3c1a6-103">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="3c1a6-103">ConvertFrom-Markdown</span></span>

## <span data-ttu-id="3c1a6-104">개요</span><span class="sxs-lookup"><span data-stu-id="3c1a6-104">SYNOPSIS</span></span>
<span data-ttu-id="3c1a6-105">문자열 또는 파일의 내용을 **Markdowninfo** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-105">Convert the contents of a string or a file to a **MarkdownInfo** object.</span></span>

## <span data-ttu-id="3c1a6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c1a6-106">SYNTAX</span></span>

### <span data-ttu-id="3c1a6-107">PathParamSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="3c1a6-107">PathParamSet (Default)</span></span>

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="3c1a6-108">LiteralParamSet</span><span class="sxs-lookup"><span data-stu-id="3c1a6-108">LiteralParamSet</span></span>

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="3c1a6-109">InputObjParamSet</span><span class="sxs-lookup"><span data-stu-id="3c1a6-109">InputObjParamSet</span></span>

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## <span data-ttu-id="3c1a6-110">설명</span><span class="sxs-lookup"><span data-stu-id="3c1a6-110">DESCRIPTION</span></span>

<span data-ttu-id="3c1a6-111">이 cmdlet은 지정 된 콘텐츠를 **Markdowninfo** 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-111">This cmdlet converts the specified content into a **MarkdownInfo** .</span></span> <span data-ttu-id="3c1a6-112">**Path** 매개 변수에 대 한 파일 경로가 지정 된 경우 파일의 내용이 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-112">When a file path is specified for the **Path** parameter, the contents on the file are converted.</span></span> <span data-ttu-id="3c1a6-113">Output 개체에는 다음과 같은 세 가지 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-113">The output object has three properties:</span></span>

- <span data-ttu-id="3c1a6-114">**Token** 속성에는 변환 된 개체의 AST (추상 구문 트리)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-114">The **Token** property has the abstract syntax tree (AST) of the the converted object</span></span>
- <span data-ttu-id="3c1a6-115">**Html** 속성이 지정 된 입력을 html로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-115">The **Html** property has the HTML conversion of the specified input</span></span>
- <span data-ttu-id="3c1a6-116">**AsVT100EncodedString** 매개 변수가 지정 된 경우 **VT100EncodedString** 속성에는 ANSI (VT100) 이스케이프 시퀀스가 있는 변환 된 문자열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-116">The **VT100EncodedString** property has the converted string with ANSI (VT100) escape sequences if the **AsVT100EncodedString** parameter was specified</span></span>

<span data-ttu-id="3c1a6-117">이 cmdlet은 PowerShell 6.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="3c1a6-118">예제</span><span class="sxs-lookup"><span data-stu-id="3c1a6-118">EXAMPLES</span></span>

### <span data-ttu-id="3c1a6-119">예제 1: Markdown 콘텐츠를 포함 하는 파일을 HTML로 변환</span><span class="sxs-lookup"><span data-stu-id="3c1a6-119">Example 1: Convert a file containing Markdown content to HTML</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md
```

<span data-ttu-id="3c1a6-120">**Markdowninfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-120">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="3c1a6-121">**Tokens** 속성에는 파일의 변환 된 내용이 포함 된 AST가 있습니다 `README.md` .</span><span class="sxs-lookup"><span data-stu-id="3c1a6-121">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="3c1a6-122">**Html** 속성에는 파일의 html 변환 내용이 포함 되어 `README.md` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-122">The **Html** property has the HTML converted content of the `README.md` file.</span></span>

### <span data-ttu-id="3c1a6-123">예제 2: Markdown 콘텐츠를 포함 하는 파일을 VT100 인코딩된 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="3c1a6-123">Example 2: Convert a file containing Markdown content to a VT100-encoded string</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

<span data-ttu-id="3c1a6-124">**Markdowninfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-124">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="3c1a6-125">**Tokens** 속성에는 파일의 변환 된 내용이 포함 된 AST가 있습니다 `README.md` .</span><span class="sxs-lookup"><span data-stu-id="3c1a6-125">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="3c1a6-126">**VT100EncodedString** 속성은 파일의 VT100 인코딩된 문자열 변환 된 콘텐츠를 포함 합니다 `README.md` .</span><span class="sxs-lookup"><span data-stu-id="3c1a6-126">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="3c1a6-127">예제 3: Markdown 콘텐츠를 포함 하는 입력 개체를 VT100 인코딩된 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="3c1a6-127">Example 3: Convert input object containing Markdown content to a VT100-encoded string</span></span>

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="3c1a6-128">**Markdowninfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-128">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="3c1a6-129">에서 **FileInfo** 개체는 `Get-Item` VT100 인코딩된 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-129">The **FileInfo** object from `Get-Item` is converted to a VT100-encoded string.</span></span> <span data-ttu-id="3c1a6-130">**Tokens** 속성에는 파일의 변환 된 내용이 포함 된 AST가 있습니다 `README.md` .</span><span class="sxs-lookup"><span data-stu-id="3c1a6-130">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="3c1a6-131">**VT100EncodedString** 속성은 파일의 VT100 인코딩된 문자열 변환 된 콘텐츠를 포함 합니다 `README.md` .</span><span class="sxs-lookup"><span data-stu-id="3c1a6-131">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="3c1a6-132">예제 4: Markdown 콘텐츠를 포함 하는 문자열을 VT100 인코딩된 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="3c1a6-132">Example 4: Convert a string containing Markdown content to a VT100-encoded string</span></span>

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="3c1a6-133">**Markdowninfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-133">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="3c1a6-134">지정 된 문자열은 `**Bold text**` VT100 인코딩 문자열로 변환 되 고 **VT100EncodedString** 속성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-134">The specified string `**Bold text**` is converted to a VT100-encoded string and available in **VT100EncodedString** property.</span></span>

## <span data-ttu-id="3c1a6-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c1a6-135">PARAMETERS</span></span>

### <span data-ttu-id="3c1a6-136">-AsVT100EncodedString</span><span class="sxs-lookup"><span data-stu-id="3c1a6-136">-AsVT100EncodedString</span></span>

<span data-ttu-id="3c1a6-137">출력을 VT100 이스케이프 코드가 포함 된 문자열로 인코딩해야 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-137">Specifies if the output should be encoded as a string with VT100 escape codes.</span></span>

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

### <span data-ttu-id="3c1a6-138">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3c1a6-138">-InputObject</span></span>

<span data-ttu-id="3c1a6-139">변환할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-139">Specifies the object to be converted.</span></span> <span data-ttu-id="3c1a6-140">**System.string** 형식의 개체가 지정 되 면 문자열이 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-140">When an object of type **System.String** is specified, the string is converted.</span></span> <span data-ttu-id="3c1a6-141">**System.object** 형식의 개체가 지정 되 면 개체에서 지정 된 파일의 내용이 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-141">When an object of type **System.IO.FileInfo** is specified, the contents of the file specified by the object are converted.</span></span> <span data-ttu-id="3c1a6-142">다른 형식의 개체는 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-142">Objects of any other type result in an error.</span></span>

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

### <span data-ttu-id="3c1a6-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3c1a6-143">-LiteralPath</span></span>

<span data-ttu-id="3c1a6-144">변환할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-144">Specifies a path to the file to be converted.</span></span>

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

### <span data-ttu-id="3c1a6-145">-Path</span><span class="sxs-lookup"><span data-stu-id="3c1a6-145">-Path</span></span>

<span data-ttu-id="3c1a6-146">변환할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-146">Specifies a path to the file to be converted.</span></span>

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

### <span data-ttu-id="3c1a6-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c1a6-147">CommonParameters</span></span>

<span data-ttu-id="3c1a6-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c1a6-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c1a6-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c1a6-150">입력</span><span class="sxs-lookup"><span data-stu-id="3c1a6-150">INPUTS</span></span>

### <span data-ttu-id="3c1a6-151">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="3c1a6-151">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="3c1a6-152">출력</span><span class="sxs-lookup"><span data-stu-id="3c1a6-152">OUTPUTS</span></span>

### <span data-ttu-id="3c1a6-153">Microsoft. PowerShell. MarkdownRender. Markdownrender</span><span class="sxs-lookup"><span data-stu-id="3c1a6-153">Microsoft.PowerShell.MarkdownRender.MarkdownInfo</span></span>

## <span data-ttu-id="3c1a6-154">참고</span><span class="sxs-lookup"><span data-stu-id="3c1a6-154">NOTES</span></span>

## <span data-ttu-id="3c1a6-155">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3c1a6-155">RELATED LINKS</span></span>

[<span data-ttu-id="3c1a6-156">Markdown 파서</span><span class="sxs-lookup"><span data-stu-id="3c1a6-156">Markdown Parser</span></span>](https://github.com/lunet-io/markdig)

[<span data-ttu-id="3c1a6-157">ANSI 이스케이프 코드</span><span class="sxs-lookup"><span data-stu-id="3c1a6-157">ANSI escape code</span></span>](https://wikipedia.org/wiki/ANSI_escape_code)
