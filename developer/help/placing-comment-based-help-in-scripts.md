---
title: 스크립트에서 주석 기반 도움말을 배치 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860769"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="5598d-102">스크립트에 설명 기반 도움말 배치</span><span class="sxs-lookup"><span data-stu-id="5598d-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="5598d-103">이 항목에서는 스크립트에 대 한 설명 기반 도움말을 배치 하는 위치를 설명 하는 `Get-Help` cmdlet 스크립트와 스크립트에 있을 수 있는 모든 함수를 사용 하 여 하지 설명 기반 도움말 항목을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="5598d-104">스크립트에 대 한 설명 기반 도움말을 배치 하는 위치</span><span class="sxs-lookup"><span data-stu-id="5598d-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="5598d-105">스크립트 파일의 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-105">At the beginning of the script file.</span></span> <span data-ttu-id="5598d-106">스크립트 도움말 스크립트에서 주석 및 빈 줄에 의해서만 올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="5598d-107">스크립트 파일의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-107">At the end of the script file.</span></span>

  <span data-ttu-id="5598d-108">함수 선언 (도움말) 한 후 스크립트 본문의 첫 번째 항목을 사용 하는 경우 도움말 스크립트의 끝 사이의 함수 선언 두 개 이상의 빈 줄 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="5598d-109">이 고, 그렇지 도움말은 도움말 스크립트에 대 한 도움말이 없습니다 함수에 대 한 것으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="5598d-110">도움말 배치 스크립트에서의 예</span><span class="sxs-lookup"><span data-stu-id="5598d-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="5598d-111">다음 예제에서는 각 스크립트에 대 한 설명 기반 도움말에 대 한 배치 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="5598d-112">스크립트의 시작 부분에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="5598d-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="5598d-113">다음 예제에서는 스크립트의 시작 부분에서 주석 기반를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="5598d-114">스크립트의 끝에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="5598d-114">Help at the End of a Script</span></span>

 <span data-ttu-id="5598d-115">다음 예제에서는 스크립트의 끝 주석 기반 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5598d-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```