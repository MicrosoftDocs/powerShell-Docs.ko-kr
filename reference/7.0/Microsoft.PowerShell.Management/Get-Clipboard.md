---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: ed56dc5655f640dae1d80c66850581ff12dbb7ee
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347604"
---
# <span data-ttu-id="5f094-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="5f094-103">Get-Clipboard</span></span>

## <span data-ttu-id="5f094-104">개요</span><span class="sxs-lookup"><span data-stu-id="5f094-104">SYNOPSIS</span></span>
<span data-ttu-id="5f094-105">클립보드의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="5f094-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f094-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="5f094-107">설명</span><span class="sxs-lookup"><span data-stu-id="5f094-107">DESCRIPTION</span></span>

<span data-ttu-id="5f094-108">`Get-Clipboard`Cmdlet은 클립보드의 내용을 텍스트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="5f094-109">텍스트의 여러 줄은와 유사한 문자열 배열로 반환 됩니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="5f094-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="5f094-110">Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span> <span data-ttu-id="5f094-111">이 cmdlet은 macOS에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-111">This cmdlet is not supported on macOS.</span></span>

## <span data-ttu-id="5f094-112">예제</span><span class="sxs-lookup"><span data-stu-id="5f094-112">EXAMPLES</span></span>

### <span data-ttu-id="5f094-113">예제 1: 클립보드의 내용 가져오기 및 명령줄에 표시</span><span class="sxs-lookup"><span data-stu-id="5f094-113">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="5f094-114">이 예제에서는 "hello" 텍스트를 클립보드에 복사 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-114">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="5f094-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f094-115">PARAMETERS</span></span>

### <span data-ttu-id="5f094-116">-Raw</span><span class="sxs-lookup"><span data-stu-id="5f094-116">-Raw</span></span>

<span data-ttu-id="5f094-117">클립보드의 전체 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-117">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="5f094-118">여러 줄 텍스트는 문자열 배열이 아니라 단일 여러 줄 문자열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f094-118">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="5f094-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f094-119">CommonParameters</span></span>

<span data-ttu-id="5f094-120">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f094-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f094-121">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f094-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f094-122">입력</span><span class="sxs-lookup"><span data-stu-id="5f094-122">INPUTS</span></span>

## <span data-ttu-id="5f094-123">출력</span><span class="sxs-lookup"><span data-stu-id="5f094-123">OUTPUTS</span></span>

### <span data-ttu-id="5f094-124">System.String</span><span class="sxs-lookup"><span data-stu-id="5f094-124">System.String</span></span>

## <span data-ttu-id="5f094-125">참고</span><span class="sxs-lookup"><span data-stu-id="5f094-125">NOTES</span></span>

## <span data-ttu-id="5f094-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5f094-126">RELATED LINKS</span></span>

[<span data-ttu-id="5f094-127">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="5f094-127">Set-Clipboard</span></span>](Set-Clipboard.md)
