---
description: '`InlineScript`워크플로에서 PowerShell 명령을 실행 하는 작업에 대해 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_inlinescript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_InlineScript
ms.openlocfilehash: 2eaeb02c6441865551b586e27a39c4000826752b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221905"
---
# <a name="about-inlinescript"></a><span data-ttu-id="5aba2-104">InlineScript 정보</span><span class="sxs-lookup"><span data-stu-id="5aba2-104">About InlineScript</span></span>

## <a name="short-description"></a><span data-ttu-id="5aba2-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5aba2-105">Short description</span></span>

<span data-ttu-id="5aba2-106">`InlineScript`워크플로에서 PowerShell 명령을 실행 하는 작업에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-106">Describes the `InlineScript` activity, that runs PowerShell commands in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="5aba2-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-107">Long description</span></span>

<span data-ttu-id="5aba2-108">`InlineScript`활동은 공유 PowerShell 세션의 워크플로에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-108">The `InlineScript` activity runs commands in a shared PowerShell session's workflow.</span></span> <span data-ttu-id="5aba2-109">`InlineScript` 는 워크플로에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-109">`InlineScript` is only valid in workflows.</span></span>

## <a name="syntax"></a><span data-ttu-id="5aba2-110">구문</span><span class="sxs-lookup"><span data-stu-id="5aba2-110">Syntax</span></span>

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a><span data-ttu-id="5aba2-111">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="5aba2-111">Detailed description</span></span>

<span data-ttu-id="5aba2-112">`InlineScript`활동은 공유 PowerShell 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-112">The `InlineScript` activity runs commands in a shared PowerShell session.</span></span> <span data-ttu-id="5aba2-113">워크플로에이를 포함 하 여 워크플로에서 유효 하지 않은 데이터 및 명령을 공유 하는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-113">You can include it in a workflow to run commands that share data and commands that aren't otherwise valid in a workflow.</span></span>

<span data-ttu-id="5aba2-114">`InlineScript`스크립트 블록은 모든 유효한 PowerShell 명령 및 식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-114">The `InlineScript` script block can include all valid PowerShell commands and expressions.</span></span> <span data-ttu-id="5aba2-115">스크립트 블록의 명령 및 식은 `InlineScript` 동일한 세션에서 실행 되므로 가져온 모듈 및 변수 값을 포함 하 여 모든 상태 및 데이터를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-115">Because the commands and expressions in an `InlineScript` script block run in the same session, they share all state and data, including imported modules and the values of variables.</span></span>

<span data-ttu-id="5aba2-116">`InlineScript`루프 또는 제어 문이나 병렬 또는 시퀀스 스크립트 블록 내부를 포함 하 여 워크플로 또는 중첩 된 워크플로의 아무 곳에 나 활동을 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-116">You can place an `InlineScript` activity anywhere in a workflow or nested workflow, including inside a loop or control statement or a Parallel or Sequence script block.</span></span>

<span data-ttu-id="5aba2-117">활동에는 `InlineScript` **pspersist** 를 비롯 한 활동 일반 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-117">The `InlineScript` activity has the activity common parameters, including **PSPersist**.</span></span> <span data-ttu-id="5aba2-118">그러나 스크립트 블록의 명령 및 식에는 `InlineScript` 검사점, 지 속성, 워크플로 또는 활동 일반 매개 변수와 같은 워크플로 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-118">However, the commands and expressions in an `InlineScript` script block don't have the workflow features such as checkpointing, or persistence, and workflow or activity common parameters.</span></span> <span data-ttu-id="5aba2-119">자세한 내용은 [about_ActivityCommonParameters](about_ActivityCommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5aba2-119">For more information, see [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span></span>

## <a name="inlinescript-variables"></a><span data-ttu-id="5aba2-120">InlineScript 변수</span><span class="sxs-lookup"><span data-stu-id="5aba2-120">InlineScript Variables</span></span>

<span data-ttu-id="5aba2-121">기본적으로 워크플로에 정의 된 변수는 스크립트 블록의 명령에 표시 되지 않습니다 `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="5aba2-121">By default, the variables that are defined in a workflow aren't visible to the commands in the `InlineScript` script block.</span></span> <span data-ttu-id="5aba2-122">워크플로 변수가에 표시 되도록 하려면 `InlineScript` 범위 한정자를 사용 `$Using` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-122">To make workflow variables visible to the `InlineScript`, use the `$Using` scope modifier.</span></span> <span data-ttu-id="5aba2-123">`$Using`범위 한정자는의 각 변수에 대해 한 번만 필요 합니다 `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="5aba2-123">The `$Using` scope modifier is required only once for each variable in the `InlineScript`.</span></span>

<span data-ttu-id="5aba2-124">범위 한정자에 대 한 자세한 내용은 `$Using` [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5aba2-124">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

<span data-ttu-id="5aba2-125">다음 예에서는 `$Using` 범위 한정자를 사용 하 여 `$a` 스크립트 블록의 명령에서 최상위 워크플로 변수 값을 사용 하도록 설정 하는 방법을 보여 줍니다 `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="5aba2-125">The following example shows that the `$Using` scope modifier makes the value of the `$a` top-level workflow variable available to the commands in the `InlineScript` script block.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ## Without $Using, the $a workflow variable isn't visible
  ## in inline script.
  InlineScript {"Inline A0 = $a"}

  ## $Using imports the variable and its current value.
  InlineScript {"Inline A1 = $Using:a"}
}

Test-Workflow
```

```output
Inline A0 =
Inline A1 = 3
```

## <a name="returning-variables-in-inlinescript"></a><span data-ttu-id="5aba2-126">InlineScript의 변수 반환</span><span class="sxs-lookup"><span data-stu-id="5aba2-126">Returning variables in InlineScript</span></span>

<span data-ttu-id="5aba2-127">`InlineScript` 명령은 워크플로 범위에서 가져온 변수의 값을 변경할 수 있지만 변경 내용이 워크플로 범위에 표시 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-127">`InlineScript` commands can change the value of the variable that was imported from workflow scope, but the changes aren't visible in workflow scope.</span></span> <span data-ttu-id="5aba2-128">이러한 변수를 표시하려면 다음 예제에 표시된 대로 변경된 값을 워크플로 범위로 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-128">To make them visible, return the changed value to the workflow scope, as shown in the following example.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ##  Changes to the InlineScript variable value don't
  ##  change the workflow variable.
  InlineScript {
    $a = $Using:a+1;
    "Inline A = $a"
  }
  "Workflow A = $a"

  ##  To change the variable in workflow scope, return the
  ##  new value.
  $a = InlineScript {$b = $Using:a+1; $b}
  "Workflow New A = $a"
}

Test-Workflow
```

```output
Inline A = 4
Workflow A = 3
Workflow New A = 4
```

> [!NOTE]
> <span data-ttu-id="5aba2-129">범위 한정자가 있는 문은 `$Using` 스크립트 블록에서 변수를 사용 하기 전에 나타나야 합니다 `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="5aba2-129">A statement with the `$Using` scope modifier should appear before any use of the variable in the `InlineScript` script block.</span></span>

## <a name="running-in-process"></a><span data-ttu-id="5aba2-130">In-process 실행</span><span class="sxs-lookup"><span data-stu-id="5aba2-130">Running in-process</span></span>

<span data-ttu-id="5aba2-131">안정성을 높이기 위해 스크립트 블록의 명령은 `InlineScript` 워크플로가 실행 되는 프로세스와는 별도로 자체 프로세스에서 실행 된 다음 해당 출력을 워크플로 프로세스로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-131">To improve reliability, the commands in the `InlineScript` script block run in their own process, separate from the process in which the workflow runs, and then return their output to the workflow process.</span></span>

<span data-ttu-id="5aba2-132">PowerShell `InlineScript` 에서 워크플로 프로세스의 작업을 실행 하도록 지시 하려면 `InlineScript` cmdlet을 사용 하는 것과 같이 세션 구성의 **OutOfProcessActivity** 속성에서 값을 제거 합니다 `New-PSWorkflowExecutionOption` .</span><span class="sxs-lookup"><span data-stu-id="5aba2-132">To direct PowerShell to run the `InlineScript` activity in the workflow process, remove the `InlineScript` value from the **OutOfProcessActivity** property of the session configuration, such as by using the `New-PSWorkflowExecutionOption` cmdlet.</span></span>

### <a name="example"></a><span data-ttu-id="5aba2-133">예제</span><span class="sxs-lookup"><span data-stu-id="5aba2-133">Example</span></span>

<span data-ttu-id="5aba2-134">`InlineScript`다음 워크플로의은 PowerShell에서 유효 하지만 워크플로에서 유효 하지 않은 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-134">The `InlineScript` in the following workflow includes commands that are valid in PowerShell but aren't valid in workflows.</span></span> <span data-ttu-id="5aba2-135">예를 들어 `New-Object` cmdlet은 **ComObject** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aba2-135">For example, the `New-Object` cmdlet with the **ComObject** parameter.</span></span>

```powershell
workflow Test-Workflow
{
  $ie = InlineScript {
    $ie = New-Object -ComObject InternetExplorer.Application -Property @{navigate2="www.microsoft.com"}

    $ie.Visible = $true
  }

  $ie
}

Test-Workflow
```

## <a name="see-also"></a><span data-ttu-id="5aba2-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5aba2-136">See also</span></span>

[<span data-ttu-id="5aba2-137">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="5aba2-137">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)

[<span data-ttu-id="5aba2-138">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="5aba2-138">about_Remote_Variables</span></span>](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[<span data-ttu-id="5aba2-139">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="5aba2-139">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="5aba2-140">[Psworkflow](xref:PSWorkflow) cmdlet</span><span class="sxs-lookup"><span data-stu-id="5aba2-140">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="5aba2-141">워크플로 가이드</span><span class="sxs-lookup"><span data-stu-id="5aba2-141">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="5aba2-142">Windows PowerShell 워크플로 작성</span><span class="sxs-lookup"><span data-stu-id="5aba2-142">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
