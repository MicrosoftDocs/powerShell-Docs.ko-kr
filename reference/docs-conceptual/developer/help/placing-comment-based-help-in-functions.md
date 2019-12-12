---
title: 함수에 주석 기반 도움말 배치 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367782"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="efb66-102">함수에 설명 기반 도움말 배치</span><span class="sxs-lookup"><span data-stu-id="efb66-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="efb66-103">이 항목에서는 `Get-Help` cmdlet이 주석 기반 도움말 항목을 올바른 함수와 연결 하도록 함수에 대 한 주석 기반 도움말을 넣을 위치에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="efb66-104">함수에 대 한 주석 기반 도움말을 넣을 위치</span><span class="sxs-lookup"><span data-stu-id="efb66-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="efb66-105">함수 본문의 시작 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="efb66-106">함수 본문의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-106">At the end of the function body.</span></span>

- <span data-ttu-id="efb66-107">`Function` 키워드 앞에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-107">Before the `Function` keyword.</span></span> <span data-ttu-id="efb66-108">함수가 스크립트나 스크립트 모듈에 있는 경우 주석 기반 도움말의 마지막 줄과 `Function` 키워드 사이에 빈 줄이 둘 이상 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="efb66-109">그렇지 않으면 함수를 사용 하지 않고 도움말을 스크립트와 연결 `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="efb66-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="efb66-110">함수의 도움말 배치 예</span><span class="sxs-lookup"><span data-stu-id="efb66-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="efb66-111">다음 예제에서는 함수에 대 한 주석 기반 도움말의 세 가지 배치 옵션을 각각 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="efb66-112">함수 본문의 시작 부분에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="efb66-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="efb66-113">다음 예제에서는 함수 본문의 시작 부분에 있는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="efb66-114">함수 본문의 끝에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="efb66-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="efb66-115">다음 예제에서는 함수 본문의 끝에 있는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="efb66-116">Function 키워드 앞의 도움말</span><span class="sxs-lookup"><span data-stu-id="efb66-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="efb66-117">다음 예제에서는 함수 키워드 앞의 줄을 기반으로 하는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efb66-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```