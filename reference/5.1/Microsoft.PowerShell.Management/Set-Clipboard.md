---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214466"
---
# <span data-ttu-id="6c6ed-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="6c6ed-103">Set-Clipboard</span></span>

## <span data-ttu-id="6c6ed-104">개요</span><span class="sxs-lookup"><span data-stu-id="6c6ed-104">SYNOPSIS</span></span>
<span data-ttu-id="6c6ed-105">현재 Windows 클립보드 항목을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-105">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="6c6ed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c6ed-106">SYNTAX</span></span>

### <span data-ttu-id="6c6ed-107">String (기본값)</span><span class="sxs-lookup"><span data-stu-id="6c6ed-107">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c6ed-108">값</span><span class="sxs-lookup"><span data-stu-id="6c6ed-108">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c6ed-109">경로</span><span class="sxs-lookup"><span data-stu-id="6c6ed-109">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c6ed-110">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6c6ed-110">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6c6ed-111">설명</span><span class="sxs-lookup"><span data-stu-id="6c6ed-111">DESCRIPTION</span></span>

<span data-ttu-id="6c6ed-112">`Set-Clipboard`Cmdlet은 현재 Windows 클립보드 항목을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-112">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="6c6ed-113">예제</span><span class="sxs-lookup"><span data-stu-id="6c6ed-113">EXAMPLES</span></span>

### <span data-ttu-id="6c6ed-114">예제 1: 텍스트를 클립보드로 복사</span><span class="sxs-lookup"><span data-stu-id="6c6ed-114">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="6c6ed-115">예제 2: 디렉터리의 내용을 클립보드에 복사</span><span class="sxs-lookup"><span data-stu-id="6c6ed-115">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="6c6ed-116">이 명령은 지정 된 폴더의 내용을 클립보드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-116">This command copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## <span data-ttu-id="6c6ed-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c6ed-117">PARAMETERS</span></span>

### <span data-ttu-id="6c6ed-118">-추가</span><span class="sxs-lookup"><span data-stu-id="6c6ed-118">-Append</span></span>

<span data-ttu-id="6c6ed-119">Cmdlet에서 클립보드를 지우지 않고 내용을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-119">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="6c6ed-120">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="6c6ed-120">-AsHtml</span></span>

<span data-ttu-id="6c6ed-121">Cmdlet이 콘텐츠를 클립보드에 HTML로 렌더링 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-121">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="6c6ed-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6c6ed-122">-LiteralPath</span></span>

<span data-ttu-id="6c6ed-123">클립보드에 복사 되는 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-123">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="6c6ed-124">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-124">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="6c6ed-125">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6c6ed-126">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6c6ed-127">작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-127">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c6ed-128">-Path</span><span class="sxs-lookup"><span data-stu-id="6c6ed-128">-Path</span></span>

<span data-ttu-id="6c6ed-129">클립보드에 복사 되는 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-129">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="6c6ed-130">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-130">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6c6ed-131">-Value</span><span class="sxs-lookup"><span data-stu-id="6c6ed-131">-Value</span></span>

<span data-ttu-id="6c6ed-132">클립보드에 복사할 콘텐츠를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-132">Specifies, as a string array, the content to copy to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6c6ed-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6c6ed-133">-Confirm</span></span>

<span data-ttu-id="6c6ed-134">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6c6ed-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6c6ed-135">-WhatIf</span></span>

<span data-ttu-id="6c6ed-136">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6c6ed-137">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6c6ed-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c6ed-138">CommonParameters</span></span>

<span data-ttu-id="6c6ed-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c6ed-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6c6ed-141">입력</span><span class="sxs-lookup"><span data-stu-id="6c6ed-141">INPUTS</span></span>

### <span data-ttu-id="6c6ed-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6c6ed-142">System.String[]</span></span>

## <span data-ttu-id="6c6ed-143">출력</span><span class="sxs-lookup"><span data-stu-id="6c6ed-143">OUTPUTS</span></span>

## <span data-ttu-id="6c6ed-144">참고</span><span class="sxs-lookup"><span data-stu-id="6c6ed-144">NOTES</span></span>

<span data-ttu-id="6c6ed-145">드문 경우 지만 루프와 같이 신속 하 게 많은 값을 사용 하 여를 사용 하는 경우 `Set-Clipboard` 클립보드에서 빈 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6ed-145">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="6c6ed-146">루프에서를 사용 하 여이 문제를 해결할 수 있습니다 `Start-Sleep -Milliseconds 1` .</span><span class="sxs-lookup"><span data-stu-id="6c6ed-146">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="6c6ed-147">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6c6ed-147">RELATED LINKS</span></span>

[<span data-ttu-id="6c6ed-148">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="6c6ed-148">Get-Clipboard</span></span>](Get-Clipboard.md)
