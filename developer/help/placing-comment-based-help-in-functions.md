---
title: 함수의 주석 기반 도움말을 배치 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083198"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="632c8-102">함수에 설명 기반 도움말 배치</span><span class="sxs-lookup"><span data-stu-id="632c8-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="632c8-103">이 항목에서는 함수에 대 한 설명 기반 도움말을 배치 하는 위치를 설명 있도록는 `Get-Help` cmdlet 올바른 함수를 사용 하 여 설명 기반 도움말 항목을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="632c8-104">함수에 대 한 설명 기반 도움말을 배치 하는 위치</span><span class="sxs-lookup"><span data-stu-id="632c8-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="632c8-105">함수 본문의 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="632c8-106">함수 본문의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-106">At the end of the function body.</span></span>

- <span data-ttu-id="632c8-107">전에 `Function` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-107">Before the `Function` keyword.</span></span> <span data-ttu-id="632c8-108">함수 스크립트 또는 스크립트 모듈의 경우 없어야 둘 이상의 빈 줄 주석 기반 도움말의 마지막 줄 사이 및 `Function` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="632c8-109">그렇지 않으면 `Get-Help` 스크립트를 사용 하 여, 없습니다 함수를 사용 하 여 도움말을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="632c8-110">함수에 대 한 도움말 배치의 예</span><span class="sxs-lookup"><span data-stu-id="632c8-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="632c8-111">다음 예제에서는 각 함수에 대 한 설명 기반 도움말에 대 한 세 가지 배치 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="632c8-112">함수 본문의 시작 부분에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="632c8-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="632c8-113">다음 예제에서는 함수 본문의 시작 부분에서 주석 기반를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="632c8-114">함수 본문의 끝에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="632c8-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="632c8-115">다음 예제에서는 주석 기반 함수 본문 끝에 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="632c8-116">Function 키워드 앞 도움말</span><span class="sxs-lookup"><span data-stu-id="632c8-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="632c8-117">다음 예제에서는 function 키워드 앞에 줄의 주석 기반을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="632c8-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```