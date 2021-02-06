---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b76f7dc87105318285c930b6cd2ae4ae10c2b0e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602054"
---
# <span data-ttu-id="b9817-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-102">Exit-PSSession</span></span>

## <span data-ttu-id="b9817-103">개요</span><span class="sxs-lookup"><span data-stu-id="b9817-103">SYNOPSIS</span></span>
<span data-ttu-id="b9817-104">원격 컴퓨터와의 대화형 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="b9817-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b9817-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="b9817-106">설명</span><span class="sxs-lookup"><span data-stu-id="b9817-106">DESCRIPTION</span></span>

<span data-ttu-id="b9817-107">**종료 PSSession** cmdlet은 Enter-PSSession cmdlet을 사용 하 여 시작한 대화형 세션을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-107">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="b9817-108">**Exit** 키워드를 사용 하 여 대화형 세션을 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-108">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="b9817-109">효과는 **종료 PSSession** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-109">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="b9817-110">예제</span><span class="sxs-lookup"><span data-stu-id="b9817-110">EXAMPLES</span></span>

### <span data-ttu-id="b9817-111">예제 1: 대화형 세션 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="b9817-111">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="b9817-112">이 명령은 Server01 원격 컴퓨터와 대화형 세션을 시작한 다음 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="b9817-113">예제 2: PSSession 개체를 사용 하 여 대화형 세션 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="b9817-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="b9817-114">이러한 명령은 PowerShell 세션 (**PSSession**)을 사용 하는 Server01 컴퓨터와 대화형 세션을 시작 하 고 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="b9817-115">대화형 세션은 PowerShell 세션을 사용 하 여 시작 되었기 때문에 대화형 세션이 종료 되어도 **PSSession** 을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="b9817-116">*ComputerName* 매개 변수를 사용 하는 경우, **-PSSession** 은 대화형 세션이 종료 될 때 종료 되는 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-116">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="b9817-117">첫 번째 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-117">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="b9817-118">이 명령은 $s 변수에 **PSSession** 을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-118">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="b9817-119">두 번째 명령은 **Enter-pssession** 을 사용 하 여 $S의 **PSSession** 을 사용 하 여 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-119">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="b9817-120">세 번째 명령은 **Exit PSSession** 을 사용 하 여 대화형 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-120">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="b9817-121">마지막 명령은 $s 변수에 **PSSession** 을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-121">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="b9817-122">**상태** 속성은 **PSSession** 이 여전히 열려 있고 사용할 수 있는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="b9817-123">예 3: Exit 키워드를 사용 하 여 세션 중지</span><span class="sxs-lookup"><span data-stu-id="b9817-123">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="b9817-124">이 예에서는 **Exit** 키워드를 사용 하 여 **Enter-PSSession** 을 사용 하 여 시작한 대화형 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-124">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="b9817-125">**Exit** 키워드는 **exit PSSession** 을 사용 하는 것과 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-125">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="b9817-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9817-126">PARAMETERS</span></span>

### <span data-ttu-id="b9817-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9817-127">CommonParameters</span></span>

<span data-ttu-id="b9817-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b9817-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9817-129">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9817-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9817-130">입력</span><span class="sxs-lookup"><span data-stu-id="b9817-130">INPUTS</span></span>

### <span data-ttu-id="b9817-131">없음</span><span class="sxs-lookup"><span data-stu-id="b9817-131">None</span></span>

<span data-ttu-id="b9817-132">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b9817-133">출력</span><span class="sxs-lookup"><span data-stu-id="b9817-133">OUTPUTS</span></span>

### <span data-ttu-id="b9817-134">없음</span><span class="sxs-lookup"><span data-stu-id="b9817-134">None</span></span>

<span data-ttu-id="b9817-135">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="b9817-136">참고</span><span class="sxs-lookup"><span data-stu-id="b9817-136">NOTES</span></span>

* <span data-ttu-id="b9817-137">이 cmdlet은 일반 매개 변수만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9817-137">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="b9817-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b9817-138">RELATED LINKS</span></span>

[<span data-ttu-id="b9817-139">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="b9817-140">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="b9817-141">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="b9817-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="b9817-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b9817-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="b9817-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b9817-145">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="b9817-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="b9817-146">Remove-PSSession</span></span>](Remove-PSSession.md)

