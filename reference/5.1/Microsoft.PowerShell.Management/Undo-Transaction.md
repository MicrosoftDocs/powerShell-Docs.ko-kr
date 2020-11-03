---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214338"
---
# <span data-ttu-id="fe695-103">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="fe695-103">Undo-Transaction</span></span>

## <span data-ttu-id="fe695-104">개요</span><span class="sxs-lookup"><span data-stu-id="fe695-104">SYNOPSIS</span></span>
<span data-ttu-id="fe695-105">활성 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-105">Rolls back the active transaction.</span></span>

## <span data-ttu-id="fe695-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe695-106">SYNTAX</span></span>

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fe695-107">설명</span><span class="sxs-lookup"><span data-stu-id="fe695-107">DESCRIPTION</span></span>
<span data-ttu-id="fe695-108">**실행 취소-트랜잭션** cmdlet은 활성 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-108">The **Undo-Transaction** cmdlet rolls back the active transaction.</span></span>
<span data-ttu-id="fe695-109">트랜잭션을 롤백하면 트랜잭션의 명령에의 한 변경 내용이 취소 되 고 데이터가 원래 형식으로 복원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-109">When you roll back a transaction, the changes that were made by the commands in the transaction are discarded and the data is restored to its original form.</span></span>

<span data-ttu-id="fe695-110">트랜잭션에 여러 구독자가 포함 된 경우 **실행 취소 트랜잭션** 명령은 모든 구독자에 대 한 전체 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-110">If the transaction includes multiple subscribers, an **Undo-Transaction** command rolls back the whole transaction for all subscribers.</span></span>

<span data-ttu-id="fe695-111">기본적으로 트랜잭션의 명령에서 오류가 생성될 경우 트랜잭션은 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-111">By default, transactions are rolled back automatically if any command in the transaction generates an error.</span></span>
<span data-ttu-id="fe695-112">그러나 다른 롤백 기본 설정을 사용 하 여 트랜잭션을 시작할 수 있으며이 cmdlet을 사용 하 여 언제 든 지 활성 트랜잭션을 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-112">However, transactions can be started by using a different rollback preference and you can use this cmdlet to roll back the active transaction at any time.</span></span>

<span data-ttu-id="fe695-113">**실행 취소-트랜잭션** Cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-113">The **Undo-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="fe695-114">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe695-114">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="fe695-115">예제</span><span class="sxs-lookup"><span data-stu-id="fe695-115">EXAMPLES</span></span>

### <span data-ttu-id="fe695-116">예 1: 현재 트랜잭션 롤백</span><span class="sxs-lookup"><span data-stu-id="fe695-116">Example 1: Roll back the current transaction</span></span>

```
PS C:\> Undo-Transaction
```

<span data-ttu-id="fe695-117">이 명령은 현재 활성 트랜잭션를 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-117">This command rolls back the current, active, transaction.</span></span>

### <span data-ttu-id="fe695-118">예제 2: 트랜잭션 시작 및 롤백</span><span class="sxs-lookup"><span data-stu-id="fe695-118">Example 2: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

<span data-ttu-id="fe695-119">이 예에서는 트랜잭션을 시작한 후 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-119">This example starts a transaction and then rolls it back.</span></span>
<span data-ttu-id="fe695-120">따라서 레지스트리가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-120">As a result, no changes are made to the registry.</span></span>

### <span data-ttu-id="fe695-121">예 3: 모든 구독자에 대 한 트랜잭션 롤백</span><span class="sxs-lookup"><span data-stu-id="fe695-121">Example 3: Roll back a transaction for all subscribers</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

<span data-ttu-id="fe695-122">이 예에서는 모든 구독자가 트랜잭션을 롤백할 때 모든 구독자에 대해 전체 트랜잭션이 롤백되는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-122">This example demonstrates that when any subscriber rolls back a transaction, the whole transaction is rolled back for all subscribers.</span></span>

<span data-ttu-id="fe695-123">첫 번째 명령은 HKCU:\Software 레지스트리 키의 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-123">The first command changes the location to the HKCU:\Software registry key.</span></span>

<span data-ttu-id="fe695-124">두 번째 명령은 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-124">The second command starts a transaction.</span></span>

<span data-ttu-id="fe695-125">세 번째 명령은 New-Item cmdlet을 사용하여 새 레지스트리 키를 만든 다음</span><span class="sxs-lookup"><span data-stu-id="fe695-125">The third command uses the New-Item cmdlet to create a new registry key.</span></span>
<span data-ttu-id="fe695-126">이 명령은 *UseTransaction* 매개 변수를 사용 하 여 트랜잭션에 변경 내용을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-126">The command uses the *UseTransaction* parameter to include the change in the transaction.</span></span>

<span data-ttu-id="fe695-127">네 번째 명령은 Get-Transaction cmdlet을 사용하여 활성 트랜잭션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-127">The fourth command uses the Get-Transaction cmdlet to get the active transaction.</span></span>
<span data-ttu-id="fe695-128">이때 상태는 Active이고 가입자 수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-128">Notice that the status is Active and the subscriber count is 1.</span></span>

<span data-ttu-id="fe695-129">다섯 번째 명령은 Start-Transaction 명령을 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-129">The fifth command uses the Start-Transaction command again.</span></span>
<span data-ttu-id="fe695-130">일반적으로 기본 트랜잭션에 사용 되는 스크립트에 자체의 완전 한 트랜잭션이 포함 되는 경우 다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-130">Typically, starting a transaction while another transaction is in progress occurs when a script that is used by the main transaction includes its own complete transaction.</span></span>
<span data-ttu-id="fe695-131">이 예제는 단계에서 검사할 수 있도록 대화형으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-131">This example is performed interactively so that you can examine it in stages.</span></span>
<span data-ttu-id="fe695-132">다른 트랜잭션이 진행 중인 동안에는 **시작 트랜잭션** 명령을 실행할 때 기존 트랜잭션을 새 구독자로 조인 하면 구독자 수가 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-132">When you run a **Start-Transaction** command while another transaction is in progress, the commands join the existing transaction as a new subscriber and the subscriber count is incremented.</span></span>

<span data-ttu-id="fe695-133">여섯 번째 명령은 **Get transaction** cmdlet을 사용 하 여 활성 트랜잭션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-133">The sixth command uses the **Get-Transaction** cmdlet to get the active transaction.</span></span>
<span data-ttu-id="fe695-134">이제 가입자 수는 2가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-134">Notice that the subscriber count is now 2.</span></span>

<span data-ttu-id="fe695-135">일곱 번째 명령은 **실행 취소 트랜잭션을** 사용 하 여 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-135">The seventh command uses **Undo-Transaction** to roll back the transaction.</span></span>
<span data-ttu-id="fe695-136">이 명령은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-136">This command does not return any objects.</span></span>

<span data-ttu-id="fe695-137">최종 명령은 활성 (이 경우 가장 최근 활성 트랜잭션)을 가져오는 **Get transaction** 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-137">The final command is a **Get-Transaction** command that gets the active, or in this case, the most recently active, transaction.</span></span>
<span data-ttu-id="fe695-138">결과를 보면 트랜잭션이 롤백되고 가입자 수가 0이 되면서 모든 가입자에 대한 트랜잭션이 롤백되는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-138">The results show that the transaction is rolled back, and that the subscriber count is 0, showing that the transaction was rolled back for all subscribers.</span></span>

## <span data-ttu-id="fe695-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fe695-139">PARAMETERS</span></span>

### <span data-ttu-id="fe695-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fe695-140">-Confirm</span></span>
<span data-ttu-id="fe695-141">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-141">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe695-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fe695-142">-WhatIf</span></span>
<span data-ttu-id="fe695-143">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-143">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fe695-144">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-144">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe695-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe695-145">CommonParameters</span></span>
<span data-ttu-id="fe695-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe695-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe695-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe695-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe695-148">입력</span><span class="sxs-lookup"><span data-stu-id="fe695-148">INPUTS</span></span>

### <span data-ttu-id="fe695-149">없음</span><span class="sxs-lookup"><span data-stu-id="fe695-149">None</span></span>
<span data-ttu-id="fe695-150">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="fe695-151">출력</span><span class="sxs-lookup"><span data-stu-id="fe695-151">OUTPUTS</span></span>

### <span data-ttu-id="fe695-152">없음</span><span class="sxs-lookup"><span data-stu-id="fe695-152">None</span></span>
<span data-ttu-id="fe695-153">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="fe695-154">참고</span><span class="sxs-lookup"><span data-stu-id="fe695-154">NOTES</span></span>

* <span data-ttu-id="fe695-155">이미 커밋된 트랜잭션은 롤백할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-155">You cannot roll back a transaction that has been committed.</span></span>

  <span data-ttu-id="fe695-156">활성 트랜잭션이 아닌 트랜잭션은 롤백할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-156">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="fe695-157">다른 독립 트랜잭션을 롤백하려면 먼저 활성 트랜잭션을 커밋하거나 롤백해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-157">To roll back a different, independent transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="fe695-158">트랜잭션을 롤백하면 트랜잭션이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-158">Rolling back the transaction ends the transaction.</span></span>
<span data-ttu-id="fe695-159">트랜잭션을 다시 사용하려면 새 트랜잭션을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe695-159">To use a transaction again, you must start a new transaction.</span></span>

## <span data-ttu-id="fe695-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fe695-160">RELATED LINKS</span></span>

[<span data-ttu-id="fe695-161">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="fe695-161">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="fe695-162">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="fe695-162">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="fe695-163">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="fe695-163">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="fe695-164">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="fe695-164">Use-Transaction</span></span>](Use-Transaction.md)
