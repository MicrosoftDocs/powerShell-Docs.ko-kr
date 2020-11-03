---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214393"
---
# <span data-ttu-id="29ac1-103">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="29ac1-103">Start-Transaction</span></span>

## <span data-ttu-id="29ac1-104">개요</span><span class="sxs-lookup"><span data-stu-id="29ac1-104">SYNOPSIS</span></span>
<span data-ttu-id="29ac1-105">트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-105">Starts a transaction.</span></span>

## <span data-ttu-id="29ac1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29ac1-106">SYNTAX</span></span>

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="29ac1-107">설명</span><span class="sxs-lookup"><span data-stu-id="29ac1-107">DESCRIPTION</span></span>
<span data-ttu-id="29ac1-108">**시작-트랜잭션** cmdlet은 하나의 단위로 관리 되는 일련의 명령인 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-108">The **Start-Transaction** cmdlet starts a transaction, which is a series of commands that are managed as a unit.</span></span>
<span data-ttu-id="29ac1-109">트랜잭션을 완료 하거나 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-109">A transaction can be completed, or committed.</span></span>
<span data-ttu-id="29ac1-110">또는 트랜잭션을 통해 변경 된 모든 데이터가 원래 상태로 복원 되도록 완전히 실행 취소 하거나 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-110">Alternatively, it can be completely undone, or rolled back, so that any data changed by the transaction is restored to its original state.</span></span>
<span data-ttu-id="29ac1-111">트랜잭션의 명령은 하나의 단위로 관리되므로 모든 명령이 커밋되거나 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-111">Because the commands in a transaction are managed as a unit, either all commands are committed or all commands are rolled back.</span></span>

<span data-ttu-id="29ac1-112">기본적으로 트랜잭션의 명령에서 오류가 생성 되 면 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-112">By default, if any command in the transaction generates an error, transactions are rolled back automatically.</span></span>
<span data-ttu-id="29ac1-113">*RollbackPreference* 매개 변수를 사용 하 여이 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-113">You can use the *RollbackPreference* parameter to change this behavior.</span></span>

<span data-ttu-id="29ac1-114">트랜잭션에 사용된 cmdlet은 트랜잭션을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-114">The cmdlets used in a transaction must be designed to support transactions.</span></span>
<span data-ttu-id="29ac1-115">트랜잭션을 지 원하는 cmdlet에는 *UseTransaction* 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-115">Cmdlets that support transactions have a *UseTransaction* parameter.</span></span>
<span data-ttu-id="29ac1-116">공급자에서 트랜잭션을 수행하려면 공급자가 트랜잭션을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-116">To perform transactions in a provider, the provider must support transactions.</span></span>
<span data-ttu-id="29ac1-117">Windows Vista 이상 버전의 windows PowerShell 레지스트리 공급자는 트랜잭션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-117">The Windows PowerShell Registry provider in Windows Vista and later versions of the Windows operating system supports transactions.</span></span>
<span data-ttu-id="29ac1-118">**TransactedString** 클래스를 사용 하 여 windows PowerShell을 지 원하는 모든 버전의 windows 시스템에서 트랜잭션에 식을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-118">You can also use the **Microsoft.PowerShell.Commands.Management.TransactedString** class to include expressions in transactions on any version of the Windows system that supports Windows PowerShell.</span></span>
<span data-ttu-id="29ac1-119">다른 Windows PowerShell 공급자도 트랜잭션을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-119">Other Windows PowerShell providers can also support transactions.</span></span>

<span data-ttu-id="29ac1-120">한 번에 하나의 트랜잭션만 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-120">Only one transaction can be active at a time.</span></span>
<span data-ttu-id="29ac1-121">트랜잭션이 진행 되는 동안 새 독립 트랜잭션을 시작 하면 새 트랜잭션이 활성 트랜잭션이 되며 원본 트랜잭션을 변경 하기 전에 새 트랜잭션을 커밋하거나 롤백해야 합니다 (예를 들어,</span><span class="sxs-lookup"><span data-stu-id="29ac1-121">If you start a new, independent transaction while a transaction is in progress, the new transaction becomes the active transaction, and you must commit or roll back the new transaction before you make any changes to the original transaction.</span></span>

<span data-ttu-id="29ac1-122">**Start-Transaction** Cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-122">**Start-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="29ac1-123">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29ac1-123">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="29ac1-124">예제</span><span class="sxs-lookup"><span data-stu-id="29ac1-124">EXAMPLES</span></span>

### <span data-ttu-id="29ac1-125">예제 1: 트랜잭션 시작 및 롤백</span><span class="sxs-lookup"><span data-stu-id="29ac1-125">Example 1: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

<span data-ttu-id="29ac1-126">이들 명령은 트랜잭션을 시작한 후 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-126">These commands start and then roll back a transaction.</span></span>
<span data-ttu-id="29ac1-127">트랜잭션이 롤백되므로 레지스트리가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-127">Because the transaction is rolled back, no changes are made to the registry.</span></span>

### <span data-ttu-id="29ac1-128">예 2: 트랜잭션 시작 및 완료</span><span class="sxs-lookup"><span data-stu-id="29ac1-128">Example 2: Start and complete a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="29ac1-129">이들 명령은 전체 트랜잭션을 시작한 후 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-129">These commands start and then complete a transaction.</span></span>
<span data-ttu-id="29ac1-130">**Complete Transaction** 명령을 사용할 때까지 레지스트리가 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-130">No changes are made to the registry until the **Complete-Transaction** command is used.</span></span>

### <span data-ttu-id="29ac1-131">예제 3: 다른 롤백 기본 설정 사용</span><span class="sxs-lookup"><span data-stu-id="29ac1-131">Example 3: Use different rollback preferences</span></span>

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

<span data-ttu-id="29ac1-132">이 예에서는 *RollbackPreference* 매개 변수 값을 변경 하는 경우의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-132">This example demonstrates the effect of changing the *RollbackPreference* parameter value.</span></span>

<span data-ttu-id="29ac1-133">첫 번째 명령 집합에서 **Start Transaction** 은 *RollbackPreference* 를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-133">In the first set of commands, **Start-Transaction** does not use *RollbackPreference* .</span></span>
<span data-ttu-id="29ac1-134">따라서 기본값 (오류)이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-134">As a result, the default value (Error) is used.</span></span>
<span data-ttu-id="29ac1-135">트랜잭션 명령에 오류가 발생 하는 경우, 즉 지정 된 경로가 존재 하지 않으면 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-135">When an error occurs in a transaction command, that is, the specified path does not exist, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="29ac1-136">두 번째 명령 집합에서 **시작 트랜잭션은** 값이 Never 인 *RollbackPreference* 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-136">In the second set of commands, **Start-Transaction** uses *RollbackPreference* with a value of Never.</span></span>
<span data-ttu-id="29ac1-137">그 결과 트랜잭션 명령에 오류가 발생해도 트랜잭션이 여전히 활성 상태가 되므로 성공적으로 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-137">As a result, when an error occurs in a transaction command, the transaction is still active and can be completed successfully.</span></span>

<span data-ttu-id="29ac1-138">대부분의 트랜잭션은 오류 없이 수행 해야 하므로 일반적으로 *RollbackPreference* 의 기본값을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-138">Because most transactions must be performed without error, the default value of *RollbackPreference* is typically preferred.</span></span>

### <span data-ttu-id="29ac1-139">예 4: 트랜잭션이 진행 되는 동안이 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="29ac1-139">Example 4: Use this cmdlet while a transaction is in progress</span></span>

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="29ac1-140">이 예에서는 트랜잭션이 진행 되는 동안 **시작 트랜잭션** 사용의 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-140">This example shows the effect of using **Start-Transaction** while a transaction is in progress.</span></span>
<span data-ttu-id="29ac1-141">효과는 진행 중인 트랜잭션에 가입하는 것과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-141">The effect is much like joining the transaction in progress.</span></span>

<span data-ttu-id="29ac1-142">이는 단순화 된 명령 이지만이 시나리오는 트랜잭션이 전체 트랜잭션을 포함 하는 스크립트를 실행 해야 하는 경우에 자주 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-142">Although this is a simplified command, this scenario frequently occurs when the transaction involves running a script that includes a complete transaction.</span></span>

<span data-ttu-id="29ac1-143">첫 번째 **시작 트랜잭션** 명령은 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-143">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="29ac1-144">첫 번째 **새 항목** 명령은 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-144">The first **New-Item** command is part of the transaction.</span></span>

<span data-ttu-id="29ac1-145">두 번째 **Start transaction** 명령은 트랜잭션에 새 구독자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-145">The second **Start-Transaction** command adds a new subscriber to the transaction.</span></span>
<span data-ttu-id="29ac1-146">이제 **Get transaction** 명령은 구독자 수가 2 인 트랜잭션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-146">The **Get-Transaction** command now returns a transaction with a subscriber count of 2.</span></span>
<span data-ttu-id="29ac1-147">두 번째 **새 항목** 명령은 동일한 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-147">The second **New-Item** command is part of the same transaction.</span></span>

<span data-ttu-id="29ac1-148">전체 트랜잭션이 완료 될 때까지 레지스트리가 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-148">No changes are made to the registry until the whole transaction is completed.</span></span>
<span data-ttu-id="29ac1-149">트랜잭션을 완료 하려면 각 구독자에 대해 하나씩 두 개의 **Complete transaction** 명령을 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-149">To complete the transaction, you must enter two **Complete-Transaction** commands, one for each subscriber.</span></span>
<span data-ttu-id="29ac1-150">언제 든 지 트랜잭션을 롤백하려면 두 구독자에 대해 모든 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-150">If you were to roll back the transaction at any point, all the transaction would be rolled back for both subscribers.</span></span>

### <span data-ttu-id="29ac1-151">예 5: 진행 중인 독립 트랜잭션 시작</span><span class="sxs-lookup"><span data-stu-id="29ac1-151">Example 5: Start an independent transaction while one is in progress</span></span>

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

<span data-ttu-id="29ac1-152">이 예에서는 다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작 하기 위해 **Start transaction** 의 *독립적인* 매개 변수를 사용 하는 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-152">This example shows the effect of using the *Independent* parameter of **Start-Transaction** to start a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="29ac1-153">이 경우 원본 트랜잭션에 영향을 주지 않고 새 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-153">In this case, the new transaction is rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="29ac1-154">트랜잭션은 논리적으로 독립적이지만 한 번의 한 개의 트랜잭션만 활성 상태일 수 있으므로 원본 트랜잭션 작업을 다시 시작하기 전에 최신의 트랜잭션을 롤백하거나 커밋해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-154">Although the transactions are logically independent, because only one transaction can be active at a time, you must roll back or commit the newest transaction before resuming work on the original transaction.</span></span>

<span data-ttu-id="29ac1-155">첫 번째 명령은 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-155">The first set of commands starts a transaction.</span></span>
<span data-ttu-id="29ac1-156">**새 항목** 명령은 첫 번째 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-156">The **New-Item** command is part of the first transaction.</span></span>

<span data-ttu-id="29ac1-157">두 번째 명령 집합에서 **시작 트랜잭션** 명령은 *독립* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-157">In the second set of commands, the **Start-Transaction** command uses the *Independent* parameter.</span></span>
<span data-ttu-id="29ac1-158">다음에 나오는 **Get transaction** 명령은 활성 트랜잭션에 대 한 트랜잭션 개체 (최신 트랜잭션 개체)를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-158">The **Get-Transaction** command that follows shows the transaction object for the active transaction, which is the newest one.</span></span>
<span data-ttu-id="29ac1-159">구독자 수는 트랜잭션과 관련이 없다는 것을 보여 주는 1과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-159">The subscriber count is equal to 1, that shows that the transactions are unrelated.</span></span>

<span data-ttu-id="29ac1-160">**실행 취소-트랜잭션** 명령을 사용 하 여 활성 트랜잭션을 롤백하는 경우 원본 트랜잭션이 다시 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-160">When the active transaction is rolled back by using an **Undo-Transaction** command, the original transaction becomes active again.</span></span>

<span data-ttu-id="29ac1-161">원래 트랜잭션의 일부인 **get-itemproperty** 명령은 오류 없이 완료 되며 원래 트랜잭션은 **Complete transaction** 명령을 사용 하 여 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-161">The **New-ItemProperty** command, which is part of the original transaction, finishes without error, and the original transaction can be completed by using the **Complete-Transaction** command.</span></span>
<span data-ttu-id="29ac1-162">그 결과 레지스트리가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-162">As a result, the registry is changed.</span></span>

### <span data-ttu-id="29ac1-163">예 6: 트랜잭션의 일부가 아닌 명령 실행</span><span class="sxs-lookup"><span data-stu-id="29ac1-163">Example 6: Run commands that are not part of a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

<span data-ttu-id="29ac1-164">이 예제에서는 트랜잭션 진행 중 전송된 명령이 트랜잭션에 포함되는지 여부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-164">This example demonstrates that commands that are submitted while a transaction is in progress can be included in the transaction or not included.</span></span>
<span data-ttu-id="29ac1-165">*UseTransaction* 매개 변수를 사용 하는 명령만 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-165">Only commands that use the *UseTransaction* parameter are part of the transaction.</span></span>

<span data-ttu-id="29ac1-166">첫 번째 및 세 번째 **새 항목** 명령은 *UseTransaction* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-166">The first and third **New-Item** commands use the *UseTransaction* parameter.</span></span>
<span data-ttu-id="29ac1-167">트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-167">These commands are part of the transaction.</span></span>
<span data-ttu-id="29ac1-168">두 번째 **새 항목** 명령은 *UseTransaction* 매개 변수를 사용 하지 않으므로 트랜잭션의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-168">Because the second **New-Item** command does not use the *UseTransaction* parameter, it is not part of the transaction.</span></span>

<span data-ttu-id="29ac1-169">첫 번째 dir 명령은 효과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-169">The first dir command shows the effect.</span></span>
<span data-ttu-id="29ac1-170">두 번째 **새 항목** 명령은 즉시 완료 되지만 첫 번째 및 세 번째 **새 항목** 명령은 트랜잭션이 커밋될 때까지 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-170">The second **New-Item** command is completed immediately, but the first and third **New-Item** commands are not effective until the transaction is committed.</span></span>

<span data-ttu-id="29ac1-171">**Complete transaction** 명령은 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-171">The **Complete-Transaction** command commits the transaction.</span></span>
<span data-ttu-id="29ac1-172">그 결과 두 번째 dir 명령은 모든 새 항목이 레지스트리에 추가 된 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-172">As a result, the second dir command shows that all of the new items are added to the registry.</span></span>

### <span data-ttu-id="29ac1-173">예 7: 지정 된 시간 내에 완료 되지 않은 트랜잭션 롤백</span><span class="sxs-lookup"><span data-stu-id="29ac1-173">Example 7: Roll back a transaction that does not finish in a specified time</span></span>

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

<span data-ttu-id="29ac1-174">이 명령은 **Start transaction** 의 *Timeout* 매개 변수를 사용 하 여 2 분 이내에 완료 해야 하는 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-174">This command uses the *Timeout* parameter of **Start-Transaction** to start a transaction that must be completed within two minutes.</span></span>
<span data-ttu-id="29ac1-175">제한 시간이 만료 되 면 트랜잭션이 완료 되지 않으면 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-175">If the transaction is not finished when the time-out expires, it is rolled back automatically.</span></span>

<span data-ttu-id="29ac1-176">제한 시간이 만료 되 면 알림이 표시 되지 않지만 트랜잭션 개체의 **Status** 속성은 RolledBack로 설정 되 고 *UseTransaction* 매개 변수를 사용 하는 명령은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-176">When the time-out expires, you are not notified, but the **Status** property of the transaction object is set to RolledBack and commands that use the *UseTransaction* parameter fail.</span></span>

## <span data-ttu-id="29ac1-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29ac1-177">PARAMETERS</span></span>

### <span data-ttu-id="29ac1-178">-독립적</span><span class="sxs-lookup"><span data-stu-id="29ac1-178">-Independent</span></span>
<span data-ttu-id="29ac1-179">이 cmdlet이 진행 중인 트랜잭션과 독립적인 트랜잭션을 시작 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-179">Indicates that this cmdlet starts a transaction that is independent of any transactions in progress.</span></span>
<span data-ttu-id="29ac1-180">기본적으로 다른 트랜잭션이 진행 되는 동안에는 **Start transaction** 을 사용 하는 경우 진행 중인 트랜잭션에 새 구독자가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-180">By default, if you use **Start-Transaction** while another transaction is in progress, a new subscriber is added to the transaction in progress.</span></span>
<span data-ttu-id="29ac1-181">이 매개 변수는 세션에서 트랜잭션이 이미 진행 중인 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-181">This parameter has an effect only when a transaction is already in progress in the session.</span></span>

<span data-ttu-id="29ac1-182">기본적으로 트랜잭션이 진행 되는 동안 **시작-트랜잭션을** 사용 하면 기존 트랜잭션 개체가 다시 사용 되 고 구독자 수가 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-182">By default, if you use **Start-Transaction** while a transaction is in progress, the existing transaction object is reused and the subscriber count is incremented.</span></span>
<span data-ttu-id="29ac1-183">결과는 원본 트랜잭션 가입과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-183">The effect is much like joining the original transaction.</span></span>
<span data-ttu-id="29ac1-184">Undo-Transaction 명령은 전체 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-184">An Undo-Transaction command rolls back the whole the transaction.</span></span>
<span data-ttu-id="29ac1-185">트랜잭션을 완료하려면 각 가입자에 대해 Complete-Transaction 명령을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-185">To complete the transaction, you must enter a Complete-Transaction command for each subscriber.</span></span>
<span data-ttu-id="29ac1-186">동시에 진행 중인 트랜잭션은 거의 관련되어 있으므로 대부분의 경우 기본값을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-186">Because most transactions that are in progress at the same time are related, the default is sufficient for most uses.</span></span>

<span data-ttu-id="29ac1-187">*독립* 매개 변수를 지정 하는 경우이 cmdlet은 원본 트랜잭션에 영향을 주지 않고 완료 하거나 취소할 수 있는 새 트랜잭션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-187">If you specify the *Independent* parameter, this cmdlet creates a new transaction that can be completed or undone without affecting the original transaction.</span></span>
<span data-ttu-id="29ac1-188">그러나 한 번의 한 개의 트랜잭션만 활성 상태일 수 있으므로 새 트랜잭션을 완료하거나 롤백해야만 원본 트랜잭션을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-188">However, because only one transaction can be active at a time, you must complete or roll back the new transaction before resuming work on the original transaction.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29ac1-189">-RollbackPreference</span><span class="sxs-lookup"><span data-stu-id="29ac1-189">-RollbackPreference</span></span>
<span data-ttu-id="29ac1-190">트랜잭션이 자동으로 롤백되는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-190">Specifies the conditions under which a transaction is automatically rolled back.</span></span>
<span data-ttu-id="29ac1-191">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="29ac1-192">오류.</span><span class="sxs-lookup"><span data-stu-id="29ac1-192">Error.</span></span>
<span data-ttu-id="29ac1-193">종료되는 오류 또는 종료되지 않는 오류가 발생하면 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-193">The transaction is rolled back automatically if a terminating or non-terminating error occurs.</span></span>
- <span data-ttu-id="29ac1-194">TerminatingError.</span><span class="sxs-lookup"><span data-stu-id="29ac1-194">TerminatingError.</span></span>
<span data-ttu-id="29ac1-195">종료되는 오류가 발생하면 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-195">The transaction is rolled back automatically if a terminating error occurs.</span></span>
- <span data-ttu-id="29ac1-196">불가능</span><span class="sxs-lookup"><span data-stu-id="29ac1-196">Never.</span></span>
<span data-ttu-id="29ac1-197">트랜잭션이 자동으로 롤백되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-197">The transaction is never rolled back automatically.</span></span>

<span data-ttu-id="29ac1-198">기본값은 Error입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-198">The default value is Error.</span></span>

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29ac1-199">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="29ac1-199">-Timeout</span></span>
<span data-ttu-id="29ac1-200">트랜잭션이 활성 상태일 수 있는 최대 시간(분)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-200">Specifies the maximum time, in minutes, that the transaction is active.</span></span>
<span data-ttu-id="29ac1-201">제한 시간이 만료되면 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-201">When the time-out expires, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="29ac1-202">기본적으로 명령줄에서 시작된 트랜잭션에 대한 제한 시간은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-202">By default, there is no time-out for transactions that are started at the command line.</span></span>
<span data-ttu-id="29ac1-203">트랜잭션을 스크립트로 시작하면 기본 제한 시간은 30분입니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-203">When transactions are started by a script, the default time-out is 30 minutes.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29ac1-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="29ac1-204">-Confirm</span></span>
<span data-ttu-id="29ac1-205">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="29ac1-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="29ac1-206">-WhatIf</span></span>
<span data-ttu-id="29ac1-207">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="29ac1-208">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="29ac1-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29ac1-209">CommonParameters</span></span>
<span data-ttu-id="29ac1-210">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="29ac1-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29ac1-211">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29ac1-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29ac1-212">입력</span><span class="sxs-lookup"><span data-stu-id="29ac1-212">INPUTS</span></span>

### <span data-ttu-id="29ac1-213">없음</span><span class="sxs-lookup"><span data-stu-id="29ac1-213">None</span></span>
<span data-ttu-id="29ac1-214">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="29ac1-215">출력</span><span class="sxs-lookup"><span data-stu-id="29ac1-215">OUTPUTS</span></span>

### <span data-ttu-id="29ac1-216">없음</span><span class="sxs-lookup"><span data-stu-id="29ac1-216">None</span></span>
<span data-ttu-id="29ac1-217">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ac1-217">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="29ac1-218">참고</span><span class="sxs-lookup"><span data-stu-id="29ac1-218">NOTES</span></span>

## <span data-ttu-id="29ac1-219">관련 링크</span><span class="sxs-lookup"><span data-stu-id="29ac1-219">RELATED LINKS</span></span>

[<span data-ttu-id="29ac1-220">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="29ac1-220">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="29ac1-221">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="29ac1-221">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="29ac1-222">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="29ac1-222">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="29ac1-223">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="29ac1-223">Use-Transaction</span></span>](Use-Transaction.md)
