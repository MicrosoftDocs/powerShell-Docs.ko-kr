---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: df7f9000cf66cebce83e3146cd5c95a7d1a78bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600850"
---
# <span data-ttu-id="fb34e-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="fb34e-102">New-Guid</span></span>

## <span data-ttu-id="fb34e-103">개요</span><span class="sxs-lookup"><span data-stu-id="fb34e-103">SYNOPSIS</span></span>
<span data-ttu-id="fb34e-104">GUID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb34e-104">Creates a GUID.</span></span>

## <span data-ttu-id="fb34e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb34e-105">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="fb34e-106">설명</span><span class="sxs-lookup"><span data-stu-id="fb34e-106">DESCRIPTION</span></span>

<span data-ttu-id="fb34e-107">**새 guid** cmdlet은 임의의 guid (globally unique identifier)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb34e-107">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="fb34e-108">스크립트에 고유 ID가 필요한 경우 필요에 따라 GUID를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb34e-108">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="fb34e-109">예제</span><span class="sxs-lookup"><span data-stu-id="fb34e-109">EXAMPLES</span></span>

### <span data-ttu-id="fb34e-110">예제 1: GUID 만들기</span><span class="sxs-lookup"><span data-stu-id="fb34e-110">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="fb34e-111">이 명령은 임의의 GUID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb34e-111">This command creates a random GUID.</span></span>
<span data-ttu-id="fb34e-112">또는 스크립트의 다른 곳에서 사용 하기 위해이 cmdlet의 출력을 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb34e-112">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="fb34e-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb34e-113">PARAMETERS</span></span>

### <span data-ttu-id="fb34e-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb34e-114">CommonParameters</span></span>

<span data-ttu-id="fb34e-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb34e-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb34e-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb34e-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb34e-117">입력</span><span class="sxs-lookup"><span data-stu-id="fb34e-117">INPUTS</span></span>

## <span data-ttu-id="fb34e-118">출력</span><span class="sxs-lookup"><span data-stu-id="fb34e-118">OUTPUTS</span></span>

### <span data-ttu-id="fb34e-119">System.Guid</span><span class="sxs-lookup"><span data-stu-id="fb34e-119">System.Guid</span></span>

<span data-ttu-id="fb34e-120">이 cmdlet은 GUID를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb34e-120">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="fb34e-121">참고</span><span class="sxs-lookup"><span data-stu-id="fb34e-121">NOTES</span></span>

## <span data-ttu-id="fb34e-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fb34e-122">RELATED LINKS</span></span>

