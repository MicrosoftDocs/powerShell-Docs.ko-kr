---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 1ee55dfaf4ecd3e46bedd8f356b1f677180c9c62
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564557"
---
# <span data-ttu-id="0b37f-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="0b37f-103">Set-Clipboard</span></span>

## <span data-ttu-id="0b37f-104">개요</span><span class="sxs-lookup"><span data-stu-id="0b37f-104">SYNOPSIS</span></span>
<span data-ttu-id="0b37f-105">클립보드의 내용을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="0b37f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0b37f-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0b37f-107">설명</span><span class="sxs-lookup"><span data-stu-id="0b37f-107">DESCRIPTION</span></span>

<span data-ttu-id="0b37f-108">`Set-Clipboard`Cmdlet은 클립보드의 내용을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="0b37f-109">Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="0b37f-110">예제</span><span class="sxs-lookup"><span data-stu-id="0b37f-110">EXAMPLES</span></span>

### <span data-ttu-id="0b37f-111">예제 1: 텍스트를 클립보드로 복사</span><span class="sxs-lookup"><span data-stu-id="0b37f-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="0b37f-112">예제 2: 파일 내용을 클립보드에 복사</span><span class="sxs-lookup"><span data-stu-id="0b37f-112">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="0b37f-113">이 예제에서는 파일 내용을 클립보드로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-113">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="0b37f-114">이 예제에서는 GitHub와 같은 다른 응용 프로그램에 붙여 넣을 수 있도록 공용 ssh 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-114">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="0b37f-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0b37f-115">PARAMETERS</span></span>

### <span data-ttu-id="0b37f-116">-추가</span><span class="sxs-lookup"><span data-stu-id="0b37f-116">-Append</span></span>

<span data-ttu-id="0b37f-117">Cmdlet에서 클립보드를 지우지 않고 내용을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-117">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="0b37f-118">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0b37f-118">-Confirm</span></span>

<span data-ttu-id="0b37f-119">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-119">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0b37f-120">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0b37f-120">-WhatIf</span></span>

<span data-ttu-id="0b37f-121">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-121">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0b37f-122">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-122">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0b37f-123">-Value</span><span class="sxs-lookup"><span data-stu-id="0b37f-123">-Value</span></span>

<span data-ttu-id="0b37f-124">클립보드에 추가할 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-124">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="0b37f-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0b37f-125">CommonParameters</span></span>

<span data-ttu-id="0b37f-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0b37f-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0b37f-127">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b37f-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0b37f-128">입력</span><span class="sxs-lookup"><span data-stu-id="0b37f-128">INPUTS</span></span>

### <span data-ttu-id="0b37f-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0b37f-129">System.String[]</span></span>

## <span data-ttu-id="0b37f-130">출력</span><span class="sxs-lookup"><span data-stu-id="0b37f-130">OUTPUTS</span></span>

## <span data-ttu-id="0b37f-131">참고</span><span class="sxs-lookup"><span data-stu-id="0b37f-131">NOTES</span></span>

<span data-ttu-id="0b37f-132">드문 경우 지만 루프와 같이 신속 하 게 많은 값을 사용 하 여를 사용 하는 경우 `Set-Clipboard` 클립보드에서 빈 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b37f-132">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="0b37f-133">루프에서를 사용 하 여이 문제를 해결할 수 있습니다 `Start-Sleep -Milliseconds 1` .</span><span class="sxs-lookup"><span data-stu-id="0b37f-133">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="0b37f-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0b37f-134">RELATED LINKS</span></span>

[<span data-ttu-id="0b37f-135">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="0b37f-135">Get-Clipboard</span></span>](Get-Clipboard.md)
