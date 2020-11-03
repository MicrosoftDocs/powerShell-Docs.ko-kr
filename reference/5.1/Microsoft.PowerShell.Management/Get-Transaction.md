---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209024"
---
# <span data-ttu-id="4e1b3-103">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="4e1b3-103">Get-Transaction</span></span>

## <span data-ttu-id="4e1b3-104">개요</span><span class="sxs-lookup"><span data-stu-id="4e1b3-104">SYNOPSIS</span></span>
<span data-ttu-id="4e1b3-105">현재(활성) 트랜잭션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-105">Gets the current (active) transaction.</span></span>

## <span data-ttu-id="4e1b3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e1b3-106">SYNTAX</span></span>

```
Get-Transaction [<CommonParameters>]
```

## <span data-ttu-id="4e1b3-107">설명</span><span class="sxs-lookup"><span data-stu-id="4e1b3-107">DESCRIPTION</span></span>
<span data-ttu-id="4e1b3-108">**Get Transaction** cmdlet은 세션의 현재 트랜잭션을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-108">The **Get-Transaction** cmdlet gets an object that represents the current transaction in the session.</span></span>

<span data-ttu-id="4e1b3-109">한 번에 하나의 트랜잭션만 활성화되기 때문에 이 cmdlet은 개체를 하나만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-109">This cmdlet never returns more than one object, because only one transaction is active at a time.</span></span>
<span data-ttu-id="4e1b3-110">독립 트랜잭션을 하나 이상 시작 하는 경우 (즉, 시작 트랜잭션의 독립 매개 변수를 사용 하 여) 가장 최근에 시작 된 트랜잭션이 활성 상태가 되 고이 트랜잭션이 **Get transaction** 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-110">If you start one or more independent transactions (by using the Independent parameter of Start-Transaction), the most recently started transaction is active, and that is the transaction that **Get-Transaction** returns.</span></span>

<span data-ttu-id="4e1b3-111">모든 활성 트랜잭션이 롤백되고 커밋되거나 커밋되면이 cmdlet은 세션에서 가장 최근에 활성화 된 트랜잭션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-111">When all active transactions have either been rolled back or committed, this cmdlet shows the transaction that was most recently active in the session.</span></span>

<span data-ttu-id="4e1b3-112">이 cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-112">This cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="4e1b3-113">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="4e1b3-114">예제</span><span class="sxs-lookup"><span data-stu-id="4e1b3-114">EXAMPLES</span></span>

### <span data-ttu-id="4e1b3-115">예 1: 현재 트랜잭션 가져오기</span><span class="sxs-lookup"><span data-stu-id="4e1b3-115">Example 1: Get the current transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="4e1b3-116">이 명령은 Get-Transaction cmdlet을 사용하여 현재 트랜잭션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-116">This command uses the Get-Transaction cmdlet to get the current transaction.</span></span>

### <span data-ttu-id="4e1b3-117">예 2: 트랜잭션 개체의 속성 및 메서드 표시</span><span class="sxs-lookup"><span data-stu-id="4e1b3-117">Example 2: Show the properties and methods of the transaction object</span></span>

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

<span data-ttu-id="4e1b3-118">이 명령은 Get-Member cmdlet을 사용하여 트랜잭션 개체의 속성과 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-118">This command uses the Get-Member cmdlet to show the properties and methods of the transaction object.</span></span>

### <span data-ttu-id="4e1b3-119">예제 3: 롤백된 트랜잭션의 속성 값 표시</span><span class="sxs-lookup"><span data-stu-id="4e1b3-119">Example 3: Show the property values of a rolled back transaction</span></span>

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

<span data-ttu-id="4e1b3-120">이 명령은 롤백된 트랜잭션에 대한 트랜잭션 개체의 속성 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-120">This command shows the property values of a transaction object for a transaction that has been rolled back.</span></span>

### <span data-ttu-id="4e1b3-121">예제 4: 커밋된 트랜잭션의 속성 값 표시</span><span class="sxs-lookup"><span data-stu-id="4e1b3-121">Example 4: Show the property values of a committed transaction</span></span>

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

<span data-ttu-id="4e1b3-122">이 명령은 커밋된 트랜잭션에 대한 트랜잭션 개체의 속성 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-122">This command shows the property values of a transaction object for a transaction that has been committed.</span></span>

### <span data-ttu-id="4e1b3-123">예 5: 다른 작업이 진행 되는 동안 트랜잭션 시작</span><span class="sxs-lookup"><span data-stu-id="4e1b3-123">Example 5: Start a transaction while another is in progress</span></span>

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

<span data-ttu-id="4e1b3-124">이 예제에서는 다른 트랜잭션이 진행되는 동안 트랜잭션을 시작할 경우 트랜잭션 개체에 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-124">This example shows the effect on the transaction object of starting a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="4e1b3-125">일반적으로 트랜잭션을 실행하는 스크립트가 함수를 포함하거나 다른 전체 트랜잭션이 포함된 스크립트를 호출하는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-125">Typically, this happens when a script that runs a transaction includes a function or calls a script that contains another complete transaction.</span></span>

<span data-ttu-id="4e1b3-126">두 번째 **시작 트랜잭션** 명령에 *독립* 매개 변수가 포함 되어 있지 않으면 **start transaction** 은 새 트랜잭션을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-126">Unless the second **Start-Transaction** command includes the *Independent* parameter, **Start-Transaction** does not create a new transaction.</span></span>
<span data-ttu-id="4e1b3-127">대신 원본 트랜잭션에 두 번째 구독자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-127">Instead, it adds a second subscriber to the original transaction.</span></span>

<span data-ttu-id="4e1b3-128">첫 번째 **시작 트랜잭션** 명령은 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-128">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="4e1b3-129">*UseTransaction* 매개 변수를 사용 하는 New-Item 명령은 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-129">A New-Item command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="4e1b3-130">두 번째 **시작 트랜잭션** 명령은 구독자를 트랜잭션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-130">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="4e1b3-131">다음 New-Item 명령도 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-131">The next New-Item command is also part of the transaction.</span></span>

<span data-ttu-id="4e1b3-132">첫 번째 **Get transaction** 명령은 다중 구독자 트랜잭션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-132">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="4e1b3-133">구독자 개수는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-133">Notice that the subscriber count is 2.</span></span>

<span data-ttu-id="4e1b3-134">첫 번째 Complete-Transaction 명령은 트랜잭션을 커밋하지 않고 구독자 개수를 1로 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-134">The first Complete-Transaction command does not commit the transaction, but it reduces the subscriber count to 1.</span></span>

<span data-ttu-id="4e1b3-135">두 번째 **Complete transaction** 명령은 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-135">The second **Complete-Transaction** command commits the transaction.</span></span>

### <span data-ttu-id="4e1b3-136">예 6: 다른 작업이 진행 되는 동안 독립 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-136">Example 6: Start an independent transaction while another is in progress</span></span>

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

<span data-ttu-id="4e1b3-137">이 예제에서는 다른 트랜잭션이 진행되는 동안 독립 트랜잭션을 시작할 경우 트랜잭션 개체에 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-137">This example shows the effect on the transaction object of starting an independent transaction while another transaction is in progress.</span></span>

<span data-ttu-id="4e1b3-138">첫 번째 **시작 트랜잭션** 명령은 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-138">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="4e1b3-139">*UseTransaction* 매개 변수를 사용 하는 **새 항목** 명령은 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-139">A **New-Item** command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="4e1b3-140">두 번째 **시작 트랜잭션** 명령은 구독자를 트랜잭션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-140">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="4e1b3-141">다음 **새 항목** 명령은 트랜잭션의 일부 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-141">The next **New-Item** command is also part of the transaction.</span></span>

<span data-ttu-id="4e1b3-142">첫 번째 **Get transaction** 명령은 다중 구독자 트랜잭션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-142">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="4e1b3-143">구독자 개수는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-143">Note that the subscriber count is 2.</span></span>

<span data-ttu-id="4e1b3-144">**Complete transaction** 명령은 구독자 수를 1로 줄인 후에는 트랜잭션을 커밋하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-144">The **Complete-Transaction** command reduces the subscriber count to 1, but it does not commit the transaction.</span></span>

<span data-ttu-id="4e1b3-145">두 번째 **Complete transaction** 명령은 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-145">The second **Complete-Transaction** command commits the transaction.</span></span>

## <span data-ttu-id="4e1b3-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e1b3-146">PARAMETERS</span></span>

### <span data-ttu-id="4e1b3-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e1b3-147">CommonParameters</span></span>
<span data-ttu-id="4e1b3-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e1b3-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e1b3-150">입력</span><span class="sxs-lookup"><span data-stu-id="4e1b3-150">INPUTS</span></span>

### <span data-ttu-id="4e1b3-151">없음</span><span class="sxs-lookup"><span data-stu-id="4e1b3-151">None</span></span>
<span data-ttu-id="4e1b3-152">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-152">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4e1b3-153">출력</span><span class="sxs-lookup"><span data-stu-id="4e1b3-153">OUTPUTS</span></span>

### <span data-ttu-id="4e1b3-154">PSTransaction.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-154">System.Management.Automation.PSTransaction</span></span>
<span data-ttu-id="4e1b3-155">이 cmdlet은 현재 트랜잭션을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e1b3-155">This cmdlet returns an object that represents the current transaction.</span></span>

## <span data-ttu-id="4e1b3-156">참고</span><span class="sxs-lookup"><span data-stu-id="4e1b3-156">NOTES</span></span>

## <span data-ttu-id="4e1b3-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4e1b3-157">RELATED LINKS</span></span>

[<span data-ttu-id="4e1b3-158">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="4e1b3-158">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="4e1b3-159">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="4e1b3-159">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="4e1b3-160">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="4e1b3-160">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="4e1b3-161">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="4e1b3-161">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="4e1b3-162">New-Item</span><span class="sxs-lookup"><span data-stu-id="4e1b3-162">New-Item</span></span>](New-Item.md)
