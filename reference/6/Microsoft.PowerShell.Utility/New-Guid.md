---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 80d30b5c3b33c3e4f8125db3a158166a00f7e816
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209152"
---
# <span data-ttu-id="30a2a-103">New-Guid</span><span class="sxs-lookup"><span data-stu-id="30a2a-103">New-Guid</span></span>

## <span data-ttu-id="30a2a-104">개요</span><span class="sxs-lookup"><span data-stu-id="30a2a-104">SYNOPSIS</span></span>
<span data-ttu-id="30a2a-105">GUID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30a2a-105">Creates a GUID.</span></span>

## <span data-ttu-id="30a2a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30a2a-106">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="30a2a-107">설명</span><span class="sxs-lookup"><span data-stu-id="30a2a-107">DESCRIPTION</span></span>

<span data-ttu-id="30a2a-108">**새 guid** cmdlet은 임의의 guid (globally unique identifier)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30a2a-108">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="30a2a-109">스크립트에 고유 ID가 필요한 경우 필요에 따라 GUID를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a2a-109">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="30a2a-110">예제</span><span class="sxs-lookup"><span data-stu-id="30a2a-110">EXAMPLES</span></span>

### <span data-ttu-id="30a2a-111">예제 1: GUID 만들기</span><span class="sxs-lookup"><span data-stu-id="30a2a-111">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="30a2a-112">이 명령은 임의의 GUID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30a2a-112">This command creates a random GUID.</span></span>
<span data-ttu-id="30a2a-113">또는 스크립트의 다른 곳에서 사용 하기 위해이 cmdlet의 출력을 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a2a-113">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="30a2a-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30a2a-114">PARAMETERS</span></span>

### <span data-ttu-id="30a2a-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30a2a-115">CommonParameters</span></span>

<span data-ttu-id="30a2a-116">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30a2a-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30a2a-117">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30a2a-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30a2a-118">입력</span><span class="sxs-lookup"><span data-stu-id="30a2a-118">INPUTS</span></span>

## <span data-ttu-id="30a2a-119">출력</span><span class="sxs-lookup"><span data-stu-id="30a2a-119">OUTPUTS</span></span>

### <span data-ttu-id="30a2a-120">System.Guid</span><span class="sxs-lookup"><span data-stu-id="30a2a-120">System.Guid</span></span>

<span data-ttu-id="30a2a-121">이 cmdlet은 GUID를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a2a-121">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="30a2a-122">참고</span><span class="sxs-lookup"><span data-stu-id="30a2a-122">NOTES</span></span>

## <span data-ttu-id="30a2a-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="30a2a-123">RELATED LINKS</span></span>
