---
ms.date: 09/12/2016
ms.topic: reference
title: 함수에 설명 기반 도움말 배치
description: 함수에 설명 기반 도움말 배치
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658202"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="f3cef-103">함수에 설명 기반 도움말 배치</span><span class="sxs-lookup"><span data-stu-id="f3cef-103">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="f3cef-104">이 항목에서는 `Get-Help` cmdlet이 주석 기반 도움말 항목과 올바른 함수를 연결 하는 함수에 대 한 주석 기반 도움말을 넣을 위치에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-104">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="f3cef-105">함수에 대 한 Comment-Based 도움말 위치</span><span class="sxs-lookup"><span data-stu-id="f3cef-105">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="f3cef-106">함수 본문의 시작 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-106">At the beginning of the function body.</span></span>

- <span data-ttu-id="f3cef-107">함수 본문의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-107">At the end of the function body.</span></span>

- <span data-ttu-id="f3cef-108">키워드 앞에 `Function` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-108">Before the `Function` keyword.</span></span> <span data-ttu-id="f3cef-109">함수가 스크립트나 스크립트 모듈에 있는 경우 주석 기반 도움말과 키워드의 마지막 줄 사이에 빈 줄이 둘 이상 있을 수 없습니다 `Function` .</span><span class="sxs-lookup"><span data-stu-id="f3cef-109">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="f3cef-110">그렇지 않으면는 `Get-Help` 함수를 사용 하지 않고 도움말을 스크립트와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-110">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="f3cef-111">함수의 도움말 배치 예</span><span class="sxs-lookup"><span data-stu-id="f3cef-111">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="f3cef-112">다음 예제에서는 함수에 대 한 주석 기반 도움말의 세 가지 배치 옵션을 각각 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-112">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="f3cef-113">함수 본문의 시작 부분에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="f3cef-113">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="f3cef-114">다음 예제에서는 함수 본문의 시작 부분에 있는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-114">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="f3cef-115">함수 본문의 끝에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="f3cef-115">Help at the End of a Function Body</span></span>

 <span data-ttu-id="f3cef-116">다음 예제에서는 함수 본문의 끝에 있는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-116">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="f3cef-117">Function 키워드 앞의 도움말</span><span class="sxs-lookup"><span data-stu-id="f3cef-117">Help Before the Function Keyword</span></span>

 <span data-ttu-id="f3cef-118">다음 예제에서는 함수 키워드 앞의 줄을 기반으로 하는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3cef-118">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
