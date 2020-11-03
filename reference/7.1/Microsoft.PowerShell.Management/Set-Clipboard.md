---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/09/2019
online version: https://go.microsoft.com/fwlink/?linkid=526220
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 6fbe7b1e5534b1227bcfd73fd58f3602186ef8c5
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239674"
---
# <span data-ttu-id="f4a91-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f4a91-103">Set-Clipboard</span></span>

## <span data-ttu-id="f4a91-104">개요</span><span class="sxs-lookup"><span data-stu-id="f4a91-104">SYNOPSIS</span></span>
<span data-ttu-id="f4a91-105">클립보드의 내용을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="f4a91-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f4a91-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f4a91-107">설명</span><span class="sxs-lookup"><span data-stu-id="f4a91-107">DESCRIPTION</span></span>

<span data-ttu-id="f4a91-108">`Set-Clipboard`Cmdlet은 클립보드의 내용을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a91-109">Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="f4a91-110">예제</span><span class="sxs-lookup"><span data-stu-id="f4a91-110">EXAMPLES</span></span>

### <span data-ttu-id="f4a91-111">예제 1: 텍스트를 클립보드로 복사</span><span class="sxs-lookup"><span data-stu-id="f4a91-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

## <span data-ttu-id="f4a91-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4a91-112">PARAMETERS</span></span>

### <span data-ttu-id="f4a91-113">-추가</span><span class="sxs-lookup"><span data-stu-id="f4a91-113">-Append</span></span>

<span data-ttu-id="f4a91-114">Cmdlet에서 클립보드를 지우지 않고 내용을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-114">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="f4a91-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f4a91-115">-Confirm</span></span>

<span data-ttu-id="f4a91-116">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f4a91-117">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f4a91-117">-WhatIf</span></span>

<span data-ttu-id="f4a91-118">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-118">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f4a91-119">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-119">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f4a91-120">-Value</span><span class="sxs-lookup"><span data-stu-id="f4a91-120">-Value</span></span>

<span data-ttu-id="f4a91-121">클립보드에 추가할 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-121">The string values to be added to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4a91-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4a91-122">CommonParameters</span></span>

<span data-ttu-id="f4a91-123">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4a91-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4a91-124">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4a91-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4a91-125">입력</span><span class="sxs-lookup"><span data-stu-id="f4a91-125">INPUTS</span></span>

### <span data-ttu-id="f4a91-126">System.String[]</span><span class="sxs-lookup"><span data-stu-id="f4a91-126">System.String[]</span></span>

## <span data-ttu-id="f4a91-127">출력</span><span class="sxs-lookup"><span data-stu-id="f4a91-127">OUTPUTS</span></span>

## <span data-ttu-id="f4a91-128">참고</span><span class="sxs-lookup"><span data-stu-id="f4a91-128">NOTES</span></span>

<span data-ttu-id="f4a91-129">드문 경우 지만 루프와 같이 신속 하 게 많은 값을 사용 하 여를 사용 하는 경우 `Set-Clipboard` 클립보드에서 빈 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4a91-129">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="f4a91-130">루프에서를 사용 하 여이 문제를 해결할 수 있습니다 `Start-Sleep -Milliseconds 1` .</span><span class="sxs-lookup"><span data-stu-id="f4a91-130">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="f4a91-131">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f4a91-131">RELATED LINKS</span></span>

[<span data-ttu-id="f4a91-132">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f4a91-132">Get-Clipboard</span></span>](Get-Clipboard.md)
