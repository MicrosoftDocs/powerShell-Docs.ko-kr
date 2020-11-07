---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: bb3f2b78fecd33288a0febd2882277721d9cf289
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342691"
---
# <span data-ttu-id="32bd4-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="32bd4-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="32bd4-104">개요</span><span class="sxs-lookup"><span data-stu-id="32bd4-104">SYNOPSIS</span></span>
<span data-ttu-id="32bd4-105">시스템 및 운영 체제 속성의 통합 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="32bd4-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="32bd4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32bd4-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="32bd4-107">설명</span><span class="sxs-lookup"><span data-stu-id="32bd4-107">DESCRIPTION</span></span>

<span data-ttu-id="32bd4-108">`Get-ComputerInfo`Cmdlet은 시스템 및 운영 체제 속성의 통합 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="32bd4-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="32bd4-109">이 cmdlet은 Windows PowerShell 5.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="32bd4-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="32bd4-110">예제</span><span class="sxs-lookup"><span data-stu-id="32bd4-110">EXAMPLES</span></span>

### <span data-ttu-id="32bd4-111">예제 1: 모든 컴퓨터 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="32bd4-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="32bd4-112">이 명령은 컴퓨터에서 모든 시스템 및 운영 체제 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="32bd4-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="32bd4-113">예제 2: 모든 컴퓨터 운영 체제 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="32bd4-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="32bd4-114">이 명령은 컴퓨터에서 모든 운영 체제 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="32bd4-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="32bd4-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32bd4-115">PARAMETERS</span></span>

### <span data-ttu-id="32bd4-116">-속성</span><span class="sxs-lookup"><span data-stu-id="32bd4-116">-Property</span></span>

<span data-ttu-id="32bd4-117">이 cmdlet이 표시 되는 컴퓨터 속성을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bd4-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="32bd4-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32bd4-118">CommonParameters</span></span>

<span data-ttu-id="32bd4-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32bd4-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32bd4-120">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32bd4-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="32bd4-121">입력</span><span class="sxs-lookup"><span data-stu-id="32bd4-121">INPUTS</span></span>

### <span data-ttu-id="32bd4-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="32bd4-122">System.String[]</span></span>

## <span data-ttu-id="32bd4-123">출력</span><span class="sxs-lookup"><span data-stu-id="32bd4-123">OUTPUTS</span></span>

### <span data-ttu-id="32bd4-124">Microsoft. PowerShell. 관리 정보</span><span class="sxs-lookup"><span data-stu-id="32bd4-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="32bd4-125">참고</span><span class="sxs-lookup"><span data-stu-id="32bd4-125">NOTES</span></span>

## <span data-ttu-id="32bd4-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="32bd4-126">RELATED LINKS</span></span>
