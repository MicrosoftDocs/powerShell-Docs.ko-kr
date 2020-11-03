---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93220033"
---
# <span data-ttu-id="2877c-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="2877c-103">Get-Clipboard</span></span>

## <span data-ttu-id="2877c-104">개요</span><span class="sxs-lookup"><span data-stu-id="2877c-104">SYNOPSIS</span></span>
<span data-ttu-id="2877c-105">현재 Windows 클립보드 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-105">Gets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="2877c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2877c-106">SYNTAX</span></span>

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="2877c-107">설명</span><span class="sxs-lookup"><span data-stu-id="2877c-107">DESCRIPTION</span></span>

<span data-ttu-id="2877c-108">`Get-Clipboard`Cmdlet은 현재 Windows 클립보드 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-108">The `Get-Clipboard` cmdlet gets the current Windows clipboard entry.</span></span> <span data-ttu-id="2877c-109">텍스트의 여러 줄은와 유사한 문자열 배열로 반환 됩니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="2877c-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

## <span data-ttu-id="2877c-110">예제</span><span class="sxs-lookup"><span data-stu-id="2877c-110">EXAMPLES</span></span>

### <span data-ttu-id="2877c-111">예제 1: 클립보드의 내용 가져오기 및 명령줄에 표시</span><span class="sxs-lookup"><span data-stu-id="2877c-111">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="2877c-112">이 예제에서는 브라우저에서 이미지를 마우스 오른쪽 단추로 클릭 하 고 **복사** 작업을 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-112">In this example we have right-clicked on an image in a browser and chose the **Copy** action.</span></span> <span data-ttu-id="2877c-113">다음 명령은 클립보드에 저장 된 이미지의 링크를 URL로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-113">The following command displays the link, as a URL, of the image that is stored in the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### <span data-ttu-id="2877c-114">예 2: 특정 형식으로 클립보드의 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="2877c-114">Example 2: Get the content of the clipboard in a specific format</span></span>

<span data-ttu-id="2877c-115">이 예제에서는 Windows에서 클립보드에 파일을 복사 하 고 <kbd>Ctrl + C</kbd>를 눌러 파일을 클립보드에 복사 Explorerby.</span><span class="sxs-lookup"><span data-stu-id="2877c-115">In this example we copied files to the clipboard in Windows Explorerby selecting them and pressing <kbd>Ctrl-C</kbd>.</span></span> <span data-ttu-id="2877c-116">다음 명령을 사용 하 여 클립보드의 내용을 파일 목록으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-116">Using the following command, you can access the contents of the clipboard as a list of files:</span></span>

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## <span data-ttu-id="2877c-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2877c-117">PARAMETERS</span></span>

### <span data-ttu-id="2877c-118">-형식</span><span class="sxs-lookup"><span data-stu-id="2877c-118">-Format</span></span>

<span data-ttu-id="2877c-119">클립보드의 형식 또는 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-119">Specifies the type, or format, of the clipboard.</span></span> <span data-ttu-id="2877c-120">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-120">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2877c-121">텍스트</span><span class="sxs-lookup"><span data-stu-id="2877c-121">Text</span></span>
- <span data-ttu-id="2877c-122">FileDropList</span><span class="sxs-lookup"><span data-stu-id="2877c-122">FileDropList</span></span>
- <span data-ttu-id="2877c-123">이미지</span><span class="sxs-lookup"><span data-stu-id="2877c-123">Image</span></span>
- <span data-ttu-id="2877c-124">오디오</span><span class="sxs-lookup"><span data-stu-id="2877c-124">Audio</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2877c-125">-Raw</span><span class="sxs-lookup"><span data-stu-id="2877c-125">-Raw</span></span>

<span data-ttu-id="2877c-126">클립보드의 전체 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-126">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="2877c-127">여러 줄 텍스트는 문자열 배열이 아니라 단일 여러 줄 문자열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-127">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="2877c-128">-TextFormatType</span><span class="sxs-lookup"><span data-stu-id="2877c-128">-TextFormatType</span></span>

<span data-ttu-id="2877c-129">클립보드의 텍스트 데이터 서식 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-129">Specifies the text data format type of the clipboard.</span></span> <span data-ttu-id="2877c-130">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2877c-131">텍스트</span><span class="sxs-lookup"><span data-stu-id="2877c-131">Text</span></span>
- <span data-ttu-id="2877c-132">UnicodeText</span><span class="sxs-lookup"><span data-stu-id="2877c-132">UnicodeText</span></span>
- <span data-ttu-id="2877c-133">형식</span><span class="sxs-lookup"><span data-stu-id="2877c-133">Rtf</span></span>
- <span data-ttu-id="2877c-134">Html</span><span class="sxs-lookup"><span data-stu-id="2877c-134">Html</span></span>
- <span data-ttu-id="2877c-135">CommaSeparatedValue</span><span class="sxs-lookup"><span data-stu-id="2877c-135">CommaSeparatedValue</span></span>

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2877c-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2877c-136">CommonParameters</span></span>

<span data-ttu-id="2877c-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2877c-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2877c-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2877c-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2877c-139">입력</span><span class="sxs-lookup"><span data-stu-id="2877c-139">INPUTS</span></span>

## <span data-ttu-id="2877c-140">출력</span><span class="sxs-lookup"><span data-stu-id="2877c-140">OUTPUTS</span></span>

### <span data-ttu-id="2877c-141">System.string, System.string, System.string, System.web. 이미지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2877c-141">System.String, System.IO.FileInfo, System.IO.Stream, System.Drawing.Image</span></span>

## <span data-ttu-id="2877c-142">참고</span><span class="sxs-lookup"><span data-stu-id="2877c-142">NOTES</span></span>

## <span data-ttu-id="2877c-143">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2877c-143">RELATED LINKS</span></span>

[<span data-ttu-id="2877c-144">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="2877c-144">Set-Clipboard</span></span>](Set-Clipboard.md)
