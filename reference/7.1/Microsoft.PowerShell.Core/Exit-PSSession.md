---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: f6123bca498d753de1fe284d48f29407c3f8a465
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209256"
---
# <span data-ttu-id="3f253-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-103">Exit-PSSession</span></span>

## <span data-ttu-id="3f253-104">개요</span><span class="sxs-lookup"><span data-stu-id="3f253-104">SYNOPSIS</span></span>
<span data-ttu-id="3f253-105">원격 컴퓨터와의 대화형 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="3f253-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3f253-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="3f253-107">설명</span><span class="sxs-lookup"><span data-stu-id="3f253-107">DESCRIPTION</span></span>

<span data-ttu-id="3f253-108">**종료 PSSession** cmdlet은 Enter-PSSession cmdlet을 사용 하 여 시작한 대화형 세션을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="3f253-109">**Exit** 키워드를 사용 하 여 대화형 세션을 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="3f253-110">효과는 **종료 PSSession** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-110">The effect is the same as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="3f253-111">예제</span><span class="sxs-lookup"><span data-stu-id="3f253-111">EXAMPLES</span></span>

### <span data-ttu-id="3f253-112">예제 1: 대화형 세션 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="3f253-112">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="3f253-113">이 명령은 Server01 원격 컴퓨터와 대화형 세션을 시작한 다음 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="3f253-114">예제 2: PSSession 개체를 사용 하 여 대화형 세션 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="3f253-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="3f253-115">이러한 명령은 PowerShell 세션 ( **PSSession** )을 사용 하는 Server01 컴퓨터와 대화형 세션을 시작 하 고 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-115">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="3f253-116">대화형 세션은 PowerShell 세션을 사용 하 여 시작 되었기 때문에 대화형 세션이 종료 되어도 **PSSession** 을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-116">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="3f253-117">*ComputerName* 매개 변수를 사용 하는 경우, **-PSSession** 은 대화형 세션이 종료 될 때 종료 되는 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="3f253-118">첫 번째 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="3f253-119">이 명령은 $s 변수에 **PSSession** 을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="3f253-120">두 번째 명령은 **Enter-pssession** 을 사용 하 여 $S의 **PSSession** 을 사용 하 여 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="3f253-121">세 번째 명령은 **Exit PSSession** 을 사용 하 여 대화형 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="3f253-122">마지막 명령은 $s 변수에 **PSSession** 을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="3f253-123">**상태** 속성은 **PSSession** 이 여전히 열려 있고 사용할 수 있는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="3f253-124">예 3: Exit 키워드를 사용 하 여 세션 중지</span><span class="sxs-lookup"><span data-stu-id="3f253-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="3f253-125">이 예에서는 **Exit** 키워드를 사용 하 여 **Enter-PSSession** 을 사용 하 여 시작한 대화형 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession** .</span></span>
<span data-ttu-id="3f253-126">**Exit** 키워드는 **exit PSSession** 을 사용 하는 것과 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-126">The **Exit** keyword has the same effect as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="3f253-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3f253-127">PARAMETERS</span></span>

### <span data-ttu-id="3f253-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3f253-128">CommonParameters</span></span>

<span data-ttu-id="3f253-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3f253-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3f253-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f253-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3f253-131">입력</span><span class="sxs-lookup"><span data-stu-id="3f253-131">INPUTS</span></span>

### <span data-ttu-id="3f253-132">없음</span><span class="sxs-lookup"><span data-stu-id="3f253-132">None</span></span>

<span data-ttu-id="3f253-133">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="3f253-134">출력</span><span class="sxs-lookup"><span data-stu-id="3f253-134">OUTPUTS</span></span>

### <span data-ttu-id="3f253-135">없음</span><span class="sxs-lookup"><span data-stu-id="3f253-135">None</span></span>

<span data-ttu-id="3f253-136">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="3f253-137">참고</span><span class="sxs-lookup"><span data-stu-id="3f253-137">NOTES</span></span>

* <span data-ttu-id="3f253-138">이 cmdlet은 일반 매개 변수만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f253-138">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="3f253-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3f253-139">RELATED LINKS</span></span>

[<span data-ttu-id="3f253-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="3f253-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="3f253-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="3f253-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="3f253-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3f253-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3f253-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="3f253-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="3f253-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="3f253-147">Remove-PSSession</span></span>](Remove-PSSession.md)

