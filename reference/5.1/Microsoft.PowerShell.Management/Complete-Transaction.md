---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215554"
---
# <span data-ttu-id="ae877-103">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="ae877-103">Complete-Transaction</span></span>

## <span data-ttu-id="ae877-104">개요</span><span class="sxs-lookup"><span data-stu-id="ae877-104">SYNOPSIS</span></span>
<span data-ttu-id="ae877-105">활성 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-105">Commits the active transaction.</span></span>

## <span data-ttu-id="ae877-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ae877-106">SYNTAX</span></span>

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ae877-107">설명</span><span class="sxs-lookup"><span data-stu-id="ae877-107">DESCRIPTION</span></span>
<span data-ttu-id="ae877-108">**Complete transaction** cmdlet은 활성 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-108">The **Complete-Transaction** cmdlet commits an active transaction.</span></span>
<span data-ttu-id="ae877-109">트랜잭션을 커밋하면 트랜잭션의 명령이 마무리되어 명령의 영향을 받는 데이터가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-109">When you commit a transaction, the commands in the transaction are finalized and the data affected by the commands is changed.</span></span>

<span data-ttu-id="ae877-110">트랜잭션에 여러 구독자가 포함 된 경우 트랜잭션을 커밋하려면 모든 Start-Transaction 명령에 대해 하나의 **Complete transaction** 명령을 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-110">If the transaction includes multiple subscribers, to commit the transaction, you must enter one **Complete-Transaction** command for every Start-Transaction command.</span></span>

<span data-ttu-id="ae877-111">**Complete-Transaction** Cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-111">The **Complete-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="ae877-112">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae877-112">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="ae877-113">예제</span><span class="sxs-lookup"><span data-stu-id="ae877-113">EXAMPLES</span></span>

### <span data-ttu-id="ae877-114">예제 1: 트랜잭션 커밋</span><span class="sxs-lookup"><span data-stu-id="ae877-114">Example 1: Commit a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

<span data-ttu-id="ae877-115">이 예에서는 **전체 트랜잭션** cmdlet을 사용 하 여 트랜잭션을 커밋하는 경우 발생 하는 상황을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-115">This example shows what happens when you use the **Complete-Transaction** cmdlet to commit a transaction.</span></span>

<span data-ttu-id="ae877-116">**Start transaction** 명령은 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-116">The **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="ae877-117">New-Item 명령은 *UseTransaction* 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-117">The New-Item command uses the *UseTransaction* parameter to include the command in the transaction.</span></span>

<span data-ttu-id="ae877-118">첫 번째 dir (Get ChildItem) 명령은 새 항목이 레지스트리에 아직 추가 되지 않은 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-118">The first dir (Get-ChildItem) command shows that the new item has not yet been added to the registry.</span></span>

<span data-ttu-id="ae877-119">**Complete transaction** 명령을 사용 하면 트랜잭션이 커밋되고 레지스트리 변경 내용이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-119">The **Complete-Transaction** command commits the transaction, which makes the registry change effective.</span></span>
<span data-ttu-id="ae877-120">그 결과 두 번째 dir 명령은 레지스트리가 변경 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-120">As a result, the second dir command shows that the registry is changed.</span></span>

### <span data-ttu-id="ae877-121">예 2: 둘 이상의 구독자가 있는 트랜잭션 커밋</span><span class="sxs-lookup"><span data-stu-id="ae877-121">Example 2: Commit a transaction that has more than one subscriber</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

<span data-ttu-id="ae877-122">이 예에서는 **Complete transaction** 을 사용 하 여 구독자가 둘 이상인 트랜잭션을 커밋하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-122">This example shows how to use **Complete-Transaction** to commit a transaction that has more than one subscriber.</span></span>

<span data-ttu-id="ae877-123">다중 구독자 트랜잭션을 커밋하려면 모든 **시작 트랜잭션** 명령에 대해 하나의 **Complete transaction** 명령을 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-123">To commit a multi-subscriber transaction, you must enter one **Complete-Transaction** command for every **Start-Transaction** command.</span></span>
<span data-ttu-id="ae877-124">데이터는 최종 **전체 트랜잭션** 명령이 전송 될 때만 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-124">The data is changed only when the final **Complete-Transaction** command is submitted.</span></span>

<span data-ttu-id="ae877-125">이 예제에서는 이해를 돕기 위해 명령줄에 입력하는 일련의 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-125">For demonstration purposes, this example shows a series of commands entered at the command line.</span></span>
<span data-ttu-id="ae877-126">실제 환경에서는 대개 스크립트로 트랜잭션을 실행하며 보조 트랜잭션은 주 스크립트로 호출되는 함수나 도우미 스크립트를 통해 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-126">In practice, transactions are likely to be run in scripts, with the secondary transaction being run by a function or helper script that is called by the main script.</span></span>

<span data-ttu-id="ae877-127">이 예에서는 **시작 트랜잭션** 명령이 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-127">In this example, a **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="ae877-128">*UseTransaction* 매개 변수를 사용 하는 **새 항목** 명령은 MyCompany 키를 소프트웨어 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-128">A **New-Item** command with the *UseTransaction* parameter adds the MyCompany key to the Software key.</span></span>
<span data-ttu-id="ae877-129">**새 항목** cmdlet은 키 개체를 반환 하지만 레지스트리의 데이터는 아직 변경 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-129">Although the **New-Item** cmdlet returns a key object, the data in the registry is not yet changed.</span></span>

<span data-ttu-id="ae877-130">두 번째 **시작 트랜잭션** 명령은 기존 트랜잭션에 두 번째 구독자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-130">A second **Start-Transaction** command adds a second subscriber to the existing transaction.</span></span>
<span data-ttu-id="ae877-131">**Get Transaction** cmdlet은 구독자 수가 2 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-131">The **Get-Transaction** cmdlet confirms that the subscriber count is 2.</span></span>
<span data-ttu-id="ae877-132">*UseTransaction* 매개 변수가 있는 New-ItemProperty 명령은 레지스트리 항목을 새 MyCompany 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-132">A New-ItemProperty command with the *UseTransaction* parameter adds a registry entry to the new MyCompany key.</span></span>
<span data-ttu-id="ae877-133">다시 명령이 값을 반환하지만 레지스트리는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-133">Again, the command returns a value, but the registry is not changed.</span></span>

<span data-ttu-id="ae877-134">첫 번째 **Complete Transaction** 명령은 구독자 수를 1만 큼 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-134">The first **Complete-Transaction** command reduces the subscriber count by 1.</span></span>
<span data-ttu-id="ae877-135">이는 **Get Transaction** 명령에 의해 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-135">This is confirmed by a **Get-Transaction** command.</span></span>
<span data-ttu-id="ae877-136">그러나 dir m \* (복합적 **item** ) 명령에의 한 데이터는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-136">However, no data is changed, as evidenced by a dir m\* ( **Get-ChildItem** ) command.</span></span>

<span data-ttu-id="ae877-137">두 번째 **Complete transaction** 명령은 전체 트랜잭션을 커밋하고 레지스트리에서 데이터를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-137">The second **Complete-Transaction** command commits the entire transaction and changes the data in the registry.</span></span>
<span data-ttu-id="ae877-138">이는 변경 내용을 표시 하는 두 번째 dir m \* 명령에 의해 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-138">This is confirmed by a second dir m\* command, which shows the changes.</span></span>

### <span data-ttu-id="ae877-139">예 3: 데이터를 변경 하지 않는 트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="ae877-139">Example 3: Perform a transaction that does not change any data</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="ae877-140">이 예에서는 \* 트랜잭션에서 Get 명령과 데이터를 변경 하지 않는 다른 명령을 사용 하는 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-140">This example shows the value of using Get-\* commands, and other commands that do not change data, in a transaction.</span></span>
<span data-ttu-id="ae877-141">트랜잭션에서 Get 명령이 사용 되는 경우 \* 트랜잭션에 포함 된 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-141">When a Get-\* command is used in a transaction, it gets the objects that are part of the transaction.</span></span>
<span data-ttu-id="ae877-142">이 경우 트랜잭션의 변경 내용을 커밋하기 전에 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-142">This allows you to preview the changes in the transaction before the changes are committed.</span></span>

<span data-ttu-id="ae877-143">이 예제에서는 트랜잭션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-143">In this example, a transaction is started.</span></span>
<span data-ttu-id="ae877-144">*UseTransaction* 매개 변수가 있는 New-Item 명령은 트랜잭션의 일부로 레지스트리에 새 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-144">A New-Item command with the *UseTransaction* parameter adds a new key to the registry as part of the transaction.</span></span>

<span data-ttu-id="ae877-145">**Complete Transaction** 명령이 실행 될 때까지 새 레지스트리 키가 레지스트리에 추가 되지 않기 때문에 간단한 Dir ( **Get-childitem** ) 명령에 새 키가 없는 레지스트리가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-145">Because the new registry key is not added to the registry until the **Complete-Transaction** command is run, a simple dir ( **Get-ChildItem** ) command shows the registry without the new key.</span></span>

<span data-ttu-id="ae877-146">그러나 *UseTransaction* 매개 변수를 dir 명령에 추가 하면이 명령은 트랜잭션의 일부가 되며 데이터에 아직 추가 되지 않은 경우에도 트랜잭션의 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-146">However, when you add the *UseTransaction* parameter to the dir command, the command becomes part of the transaction, and it gets the items in the transaction even if they are not yet added to the data.</span></span>

## <span data-ttu-id="ae877-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ae877-147">PARAMETERS</span></span>

### <span data-ttu-id="ae877-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ae877-148">-Confirm</span></span>
<span data-ttu-id="ae877-149">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ae877-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ae877-150">-WhatIf</span></span>
<span data-ttu-id="ae877-151">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ae877-152">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ae877-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ae877-153">CommonParameters</span></span>
<span data-ttu-id="ae877-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ae877-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ae877-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae877-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ae877-156">입력</span><span class="sxs-lookup"><span data-stu-id="ae877-156">INPUTS</span></span>

### <span data-ttu-id="ae877-157">없음</span><span class="sxs-lookup"><span data-stu-id="ae877-157">None</span></span>
<span data-ttu-id="ae877-158">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-158">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ae877-159">출력</span><span class="sxs-lookup"><span data-stu-id="ae877-159">OUTPUTS</span></span>

### <span data-ttu-id="ae877-160">없음</span><span class="sxs-lookup"><span data-stu-id="ae877-160">None</span></span>
<span data-ttu-id="ae877-161">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ae877-162">참고</span><span class="sxs-lookup"><span data-stu-id="ae877-162">NOTES</span></span>

* <span data-ttu-id="ae877-163">커밋된 트랜잭션을 롤백하거나 롤백된 트랜잭션을 커밋할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-163">You cannot roll back a transaction that has been committed, or commit a transaction that has been rolled back.</span></span>

  <span data-ttu-id="ae877-164">활성 트랜잭션이 아닌 트랜잭션은 롤백할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-164">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="ae877-165">다른 트랜잭션을 롤백하려면 먼저 활성 트랜잭션을 커밋하거나 롤백해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-165">To roll back a different transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="ae877-166">트랜잭션의 명령에서 오류가 발생할 경우와 같이 트랜잭션 일부를 커밋할 수 없는 경우에는 기본적으로 전체 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae877-166">By default, if any part of a transaction cannot be committed, such as when a command in the transaction results in an error, the entire transaction is rolled back.</span></span>

*

## <span data-ttu-id="ae877-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ae877-167">RELATED LINKS</span></span>

[<span data-ttu-id="ae877-168">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="ae877-168">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="ae877-169">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="ae877-169">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="ae877-170">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="ae877-170">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="ae877-171">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="ae877-171">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="ae877-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="ae877-172">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="ae877-173">New-Item</span><span class="sxs-lookup"><span data-stu-id="ae877-173">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="ae877-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae877-174">New-ItemProperty</span></span>](New-ItemProperty.md)
