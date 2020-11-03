---
description: 워크플로에서 작업을 병렬로 실행 하는 Parallel 키워드에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221890"
---
# <a name="about-parallel"></a><span data-ttu-id="ed46d-104">병렬 정보</span><span class="sxs-lookup"><span data-stu-id="ed46d-104">About Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="ed46d-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ed46d-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ed46d-106">워크플로에서 작업을 병렬로 실행 하는 Parallel 키워드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-106">Describes the Parallel keyword, which runs the activities in a workflow in parallel.</span></span>

## <a name="long-description"></a><span data-ttu-id="ed46d-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ed46d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ed46d-108">Parallel 키워드는 워크플로 작업을 병렬로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-108">The Parallel keyword runs workflow activities in parallel.</span></span> <span data-ttu-id="ed46d-109">이 키워드는 Windows PowerShell 워크플로에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-109">This keyword is valid only in  Windows PowerShell  Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="ed46d-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ed46d-110">SYNTAX</span></span>

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a><span data-ttu-id="ed46d-111">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ed46d-111">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="ed46d-112">Parallel 스크립트 블록의 명령은 동시에 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-112">The commands in a Parallel script block can run concurrently.</span></span> <span data-ttu-id="ed46d-113">실행 순서가 정해져 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-113">The order in which they run is not determined.</span></span>

<span data-ttu-id="ed46d-114">예를 들어 다음 워크플로에는 컴퓨터의 프로세스 및 서비스를 가져오는 활동을 실행하는 Parallel 스크립트 블록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-114">For example, the following workflow includes a Parallel script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="ed46d-115">Get-Process 및 Get-Service 명령은 서로 독립적 이므로 순서에 관계 없이 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-115">Because the Get-Process and Get-Service commands are independent of each other, they can run concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

<span data-ttu-id="ed46d-116">명령을 병렬로 실행 하는 것은 매우 효율적 이며 워크플로를 크게 완료 하는 데 걸리는 시간을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-116">Running commands in parallel is very efficient and reduces the time it takes to complete a workflow significantly.</span></span>

<span data-ttu-id="ed46d-117">병렬 스크립트 블록에서 선택 된 명령을 순차적으로 실행 하려면 Sequence 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-117">To run selected commands in a Parallel script block in sequential order, use the Sequence keyword.</span></span> <span data-ttu-id="ed46d-118">자세한 내용은 about_Sequence를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed46d-118">For more information, see about_Sequence.</span></span>

<span data-ttu-id="ed46d-119">컬렉션의 항목에서 Parallel 스크립트 블록을 실행 하려면 ForEach 또는 ForEach-Parallel 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46d-119">To run a Parallel script block on items in a collection, use the ForEach or ForEach -Parallel keywords.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed46d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed46d-120">SEE ALSO</span></span>

<span data-ttu-id="ed46d-121">["스크립트 워크플로 작성"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="ed46d-121">["Writing a Script Workflow"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span></span>

[<span data-ttu-id="ed46d-122">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="ed46d-122">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="ed46d-123">about_ForEach-병렬</span><span class="sxs-lookup"><span data-stu-id="ed46d-123">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="ed46d-124">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="ed46d-124">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="ed46d-125">about_Sequence</span><span class="sxs-lookup"><span data-stu-id="ed46d-125">about_Sequence</span></span>](about_Sequence.md)

[<span data-ttu-id="ed46d-126">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="ed46d-126">about_Workflows</span></span>](about_workflows.md)
