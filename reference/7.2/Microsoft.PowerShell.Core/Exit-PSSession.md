---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b1827929c53560cb261cd7b3ba1e5bd407c25700
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975093"
---
# <span data-ttu-id="7b558-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-102">Exit-PSSession</span></span>

## <span data-ttu-id="7b558-103">개요</span><span class="sxs-lookup"><span data-stu-id="7b558-103">Synopsis</span></span>
<span data-ttu-id="7b558-104">원격 컴퓨터와의 대화형 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="7b558-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7b558-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="7b558-106">Description</span><span class="sxs-lookup"><span data-stu-id="7b558-106">Description</span></span>

<span data-ttu-id="7b558-107">`Exit-PSSession`Cmdlet은 cmdlet을 사용 하 여 시작한 대화형 세션을 종료 합니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7b558-107">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="7b558-108">키워드를 사용 하 여 `exit` 대화형 세션을 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-108">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="7b558-109">효과는를 사용 하는 것과 같습니다 `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7b558-109">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="7b558-110">예</span><span class="sxs-lookup"><span data-stu-id="7b558-110">Examples</span></span>

### <span data-ttu-id="7b558-111">예제 1: 대화형 세션 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="7b558-111">Example 1: Start and stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="7b558-112">이 명령은 Server01 원격 컴퓨터와 대화형 세션을 시작한 다음 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="7b558-113">예제 2: PSSession 개체를 사용 하 여 대화형 세션 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="7b558-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="7b558-114">이러한 명령은 PowerShell 세션 (**PSSession**)을 사용 하는 Server01 컴퓨터와 대화형 세션을 시작 하 고 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="7b558-115">대화형 세션은 PowerShell 세션을 사용 하 여 시작 되었기 때문에 대화형 세션이 종료 되어도 **PSSession** 을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="7b558-116">_ComputerName_ 매개 변수를 사용 하는 경우는 `Enter-PSSession` 대화형 세션이 종료 될 때 종료 되는 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-116">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="7b558-117">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-117">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="7b558-118">이 명령은 **PSSession** 을 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="7b558-118">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="7b558-119">두 번째 명령은를 사용 하 여 `Enter-PSSession` 의 **PSSession** 을 사용 하 여 대화형 세션을 시작 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-119">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="7b558-120">세 번째 명령은 `Exit-PSSession` 를 사용 하 여 대화형 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-120">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="7b558-121">마지막 명령은 변수에 **PSSession** 을 표시 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="7b558-121">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="7b558-122">**상태** 속성은 **PSSession** 이 여전히 열려 있고 사용할 수 있는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="7b558-123">예 3: Exit 키워드를 사용 하 여 세션 중지</span><span class="sxs-lookup"><span data-stu-id="7b558-123">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="7b558-124">이 예제에서는 키워드를 사용 하 여 `exit` 를 사용 하 여 시작 된 대화형 세션을 중지 `Enter-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-124">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="7b558-125">키워드는를 `exit` 사용 하는 것과 동일한 효과를 가집니다 `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7b558-125">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="7b558-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7b558-126">Parameters</span></span>

### <span data-ttu-id="7b558-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b558-127">CommonParameters</span></span>

<span data-ttu-id="7b558-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b558-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b558-129">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b558-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b558-130">입력</span><span class="sxs-lookup"><span data-stu-id="7b558-130">Inputs</span></span>

### <span data-ttu-id="7b558-131">None</span><span class="sxs-lookup"><span data-stu-id="7b558-131">None</span></span>

<span data-ttu-id="7b558-132">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7b558-133">출력</span><span class="sxs-lookup"><span data-stu-id="7b558-133">Outputs</span></span>

### <span data-ttu-id="7b558-134">None</span><span class="sxs-lookup"><span data-stu-id="7b558-134">None</span></span>

<span data-ttu-id="7b558-135">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="7b558-136">참고</span><span class="sxs-lookup"><span data-stu-id="7b558-136">Notes</span></span>

<span data-ttu-id="7b558-137">이 cmdlet은 일반 매개 변수만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b558-137">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="7b558-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7b558-138">RELATED LINKS</span></span>

[<span data-ttu-id="7b558-139">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="7b558-140">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="7b558-141">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="7b558-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="7b558-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7b558-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="7b558-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="7b558-145">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="7b558-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7b558-146">Remove-PSSession</span></span>](Remove-PSSession.md)
