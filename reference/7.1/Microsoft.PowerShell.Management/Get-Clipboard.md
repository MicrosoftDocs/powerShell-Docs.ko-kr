---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: da1df360d7c471d925bd2f57f5258ecb2d60e631
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239984"
---
# <span data-ttu-id="3a927-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="3a927-103">Get-Clipboard</span></span>

## <span data-ttu-id="3a927-104">개요</span><span class="sxs-lookup"><span data-stu-id="3a927-104">SYNOPSIS</span></span>
<span data-ttu-id="3a927-105">클립보드의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a927-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="3a927-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3a927-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="3a927-107">설명</span><span class="sxs-lookup"><span data-stu-id="3a927-107">DESCRIPTION</span></span>

<span data-ttu-id="3a927-108">`Get-Clipboard`Cmdlet은 클립보드의 내용을 텍스트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a927-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="3a927-109">텍스트의 여러 줄은와 유사한 문자열 배열로 반환 됩니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="3a927-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="3a927-110">Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a927-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="3a927-111">예제</span><span class="sxs-lookup"><span data-stu-id="3a927-111">EXAMPLES</span></span>

### <span data-ttu-id="3a927-112">예제 1: 클립보드의 내용 가져오기 및 명령줄에 표시</span><span class="sxs-lookup"><span data-stu-id="3a927-112">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="3a927-113">이 예제에서는 "hello" 텍스트를 클립보드에 복사 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3a927-113">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="3a927-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3a927-114">PARAMETERS</span></span>

### <span data-ttu-id="3a927-115">-Raw</span><span class="sxs-lookup"><span data-stu-id="3a927-115">-Raw</span></span>

<span data-ttu-id="3a927-116">클립보드의 전체 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a927-116">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="3a927-117">여러 줄 텍스트는 문자열 배열이 아니라 단일 여러 줄 문자열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a927-117">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="3a927-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a927-118">CommonParameters</span></span>

<span data-ttu-id="3a927-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3a927-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a927-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a927-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a927-121">입력</span><span class="sxs-lookup"><span data-stu-id="3a927-121">INPUTS</span></span>

## <span data-ttu-id="3a927-122">출력</span><span class="sxs-lookup"><span data-stu-id="3a927-122">OUTPUTS</span></span>

### <span data-ttu-id="3a927-123">System.String</span><span class="sxs-lookup"><span data-stu-id="3a927-123">System.String</span></span>

## <span data-ttu-id="3a927-124">참고</span><span class="sxs-lookup"><span data-stu-id="3a927-124">NOTES</span></span>

## <span data-ttu-id="3a927-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3a927-125">RELATED LINKS</span></span>

[<span data-ttu-id="3a927-126">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="3a927-126">Set-Clipboard</span></span>](Set-Clipboard.md)

