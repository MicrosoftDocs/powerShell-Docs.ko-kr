---
description: '`ForEach -Parallel`Windows PowerShell 워크플로의 언어 구문에 대해 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 병렬 about_Foreach
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221906"
---
# <a name="about-foreach-parallel"></a><span data-ttu-id="9161e-104">Foreach-Parallel 정보</span><span class="sxs-lookup"><span data-stu-id="9161e-104">About Foreach-Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="9161e-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9161e-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9161e-106">`ForEach -Parallel`Windows PowerShell 워크플로의 언어 구문에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-106">Describes the `ForEach -Parallel` language construct in Windows PowerShell Workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="9161e-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9161e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9161e-108">키워드의 **Parallel** 매개 변수는 `ForEach` `ForEach` 지정 된 컬렉션의 각 항목에 대해 한 번씩 스크립트 블록의 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-108">The **Parallel** parameter of the `ForEach` keyword runs the commands in a `ForEach` script block once for each item in a specified collection.</span></span>

<span data-ttu-id="9161e-109">디스크 컬렉션의 디스크와 같은 컬렉션의 항목은 병렬로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-109">The items in the collection, such as a disk in a collection of disks, are processed in parallel.</span></span> <span data-ttu-id="9161e-110">스크립트 블록의 명령은 컬렉션의 각 항목에 대해 순차적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-110">The commands in the script block run sequentially on each item in the collection.</span></span>

<span data-ttu-id="9161e-111">`ForEach -Parallel` 는 Windows PowerShell 워크플로에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-111">`ForEach -Parallel` is valid only in a Windows PowerShell Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="9161e-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9161e-112">SYNTAX</span></span>

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a><span data-ttu-id="9161e-113">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9161e-113">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="9161e-114">Windows PowerShell의 ForEach 문과 마찬가지로, 컬렉션을 포함 하는 변수는 `$<collection>` 문 앞에 정의 되어야 `ForEach -Parallel` 하지만 현재 항목을 나타내는 변수는 `$<item>` 문에서 정의 됩니다 `ForEach -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="9161e-114">Like the ForEach statement in Windows PowerShell, the variable that contains collection `$<collection>` must be defined before the `ForEach -Parallel` statement, but the variable that represents the current item `$<item>` is defined in the `ForEach -Parallel` statement.</span></span>

<span data-ttu-id="9161e-115">`ForEach -Parallel`구문은 `ForEach` 키워드와 **Parallel** 매개 변수와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-115">The `ForEach -Parallel` construct is different from the `ForEach` keyword and the **Parallel** parameter.</span></span> <span data-ttu-id="9161e-116">`ForEach`키워드는 컬렉션의 항목을 순서 대로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-116">The `ForEach` keyword processes the items in the collection in sequence.</span></span> <span data-ttu-id="9161e-117">**Parallel** 매개 변수는 스크립트 블록에서 명령을 병렬로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-117">The **Parallel** parameter runs commands in a script block in parallel.</span></span> <span data-ttu-id="9161e-118">스크립트 블록에서 Parallel 스크립트 블록을 묶을 수 있습니다 `ForEach -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="9161e-118">You can enclose a Parallel script block in a `ForEach -Parallel` script block.</span></span>

<span data-ttu-id="9161e-119">**PSComputerName** 워크플로 일반 매개 변수에서 지정한 것과 같은 워크플로의 대상 컴퓨터는 항상 병렬로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-119">The target computers in a workflow, such as those specified by the **PSComputerName** workflow common parameter, are always processed in parallel.</span></span>
<span data-ttu-id="9161e-120">`ForEach -Parallel`이 목적을 위해 키워드를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-120">You do not need to specify the `ForEach -Parallel` keyword for this purpose.</span></span>

### <a name="examples"></a><span data-ttu-id="9161e-121">예제</span><span class="sxs-lookup"><span data-stu-id="9161e-121">EXAMPLES</span></span>

<span data-ttu-id="9161e-122">다음 워크플로에는 `ForEach -Parallel` 활동에서 가져오는 디스크를 처리 하는 문이 포함 되어 있습니다 `Get-Disk` .</span><span class="sxs-lookup"><span data-stu-id="9161e-122">The following workflow contains a `ForEach -Parallel` statement that processes the disks that the `Get-Disk` activity gets.</span></span> <span data-ttu-id="9161e-123">스크립트 블록의 명령은 `ForEach -Parallel` 순차적으로 실행 되지만 디스크에서 병렬로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-123">The commands in the `ForEach -Parallel` script block run sequentially, but they run on the disks in parallel.</span></span> <span data-ttu-id="9161e-124">디스크는 순서에 관계 없이 동시에 처리 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9161e-124">The disks might be processed concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="9161e-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9161e-125">SEE ALSO</span></span>

[<span data-ttu-id="9161e-126">Writing a Script Workflow</span><span class="sxs-lookup"><span data-stu-id="9161e-126">Writing a Script Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[<span data-ttu-id="9161e-127">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="9161e-127">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[<span data-ttu-id="9161e-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="9161e-128">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="9161e-129">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="9161e-129">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="9161e-130">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="9161e-130">about_Workflows</span></span>](about_Workflows.md)
