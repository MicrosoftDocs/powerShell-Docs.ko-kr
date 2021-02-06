---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: b0a9e5d1707e0d2f46c25991ddceff27d1b85287
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602067"
---
# <span data-ttu-id="f3755-102">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f3755-102">Get-Clipboard</span></span>

## <span data-ttu-id="f3755-103">개요</span><span class="sxs-lookup"><span data-stu-id="f3755-103">SYNOPSIS</span></span>
<span data-ttu-id="f3755-104">클립보드의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-104">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="f3755-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f3755-105">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="f3755-106">설명</span><span class="sxs-lookup"><span data-stu-id="f3755-106">DESCRIPTION</span></span>

<span data-ttu-id="f3755-107">`Get-Clipboard`Cmdlet은 클립보드의 내용을 텍스트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-107">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="f3755-108">텍스트의 여러 줄은와 유사한 문자열 배열로 반환 됩니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="f3755-108">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="f3755-109">Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span> <span data-ttu-id="f3755-110">이 cmdlet은 macOS에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-110">This cmdlet is not supported on macOS.</span></span>

## <span data-ttu-id="f3755-111">예제</span><span class="sxs-lookup"><span data-stu-id="f3755-111">EXAMPLES</span></span>

### <span data-ttu-id="f3755-112">예제 1: 클립보드의 내용 가져오기 및 명령줄에 표시</span><span class="sxs-lookup"><span data-stu-id="f3755-112">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="f3755-113">이 예제에서는 "hello" 텍스트를 클립보드에 복사 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-113">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="f3755-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f3755-114">PARAMETERS</span></span>

### <span data-ttu-id="f3755-115">-Raw</span><span class="sxs-lookup"><span data-stu-id="f3755-115">-Raw</span></span>

<span data-ttu-id="f3755-116">클립보드의 전체 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-116">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="f3755-117">여러 줄 텍스트는 문자열 배열이 아니라 단일 여러 줄 문자열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3755-117">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="f3755-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f3755-118">CommonParameters</span></span>

<span data-ttu-id="f3755-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f3755-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f3755-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3755-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f3755-121">입력</span><span class="sxs-lookup"><span data-stu-id="f3755-121">INPUTS</span></span>

## <span data-ttu-id="f3755-122">출력</span><span class="sxs-lookup"><span data-stu-id="f3755-122">OUTPUTS</span></span>

### <span data-ttu-id="f3755-123">System.String</span><span class="sxs-lookup"><span data-stu-id="f3755-123">System.String</span></span>

## <span data-ttu-id="f3755-124">참고</span><span class="sxs-lookup"><span data-stu-id="f3755-124">NOTES</span></span>

## <span data-ttu-id="f3755-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f3755-125">RELATED LINKS</span></span>

[<span data-ttu-id="f3755-126">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f3755-126">Set-Clipboard</span></span>](Set-Clipboard.md)
