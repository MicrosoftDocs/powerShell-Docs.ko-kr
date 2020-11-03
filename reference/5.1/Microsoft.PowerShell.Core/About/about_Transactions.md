---
description: PowerShell에서 트랜잭션 작업을 관리 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222481"
---
# <a name="about-transactions"></a><span data-ttu-id="beb4a-104">트랜잭션 정보</span><span class="sxs-lookup"><span data-stu-id="beb4a-104">About Transactions</span></span>

## <a name="short-description"></a><span data-ttu-id="beb4a-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="beb4a-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="beb4a-106">PowerShell에서 트랜잭션 작업을 관리 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-106">Describes how to manage transacted operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="beb4a-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="beb4a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="beb4a-108">트랜잭션은 PowerShell 2.0부터 PowerShell에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-108">Transactions are supported in PowerShell beginning in PowerShell 2.0.</span></span> <span data-ttu-id="beb4a-109">이 기능을 사용 하면 트랜잭션을 시작 하 고 트랜잭션에 포함 된 명령을 표시 하며 트랜잭션을 커밋하거나 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-109">This feature enables you to start a transaction, to indicate which commands are part of the transaction, and to commit or roll back a transaction.</span></span>

## <a name="about-transactions"></a><span data-ttu-id="beb4a-110">트랜잭션 정보</span><span class="sxs-lookup"><span data-stu-id="beb4a-110">ABOUT TRANSACTIONS</span></span>

<span data-ttu-id="beb4a-111">PowerShell에서 트랜잭션은 논리적 단위로 관리 되는 하나 이상의 명령 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-111">In PowerShell, a transaction is a set of one or more commands that are managed as a logical unit.</span></span> <span data-ttu-id="beb4a-112">트랜잭션의 영향을 받는 데이터를 변경 하는 트랜잭션을 완료할 수 있습니다 ("커밋됨").</span><span class="sxs-lookup"><span data-stu-id="beb4a-112">A transaction can be completed ("committed"), which changes data affected by the transaction.</span></span> <span data-ttu-id="beb4a-113">또는 트랜잭션이 완전히 취소 ("롤백") 될 수 있으므로 트랜잭션에 의해 영향을 받는 데이터가 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-113">Or, a transaction can be completely undone ("rolled back") so that the affected data is not changed by the transaction.</span></span>

<span data-ttu-id="beb4a-114">트랜잭션의 명령은 하나의 단위로 관리 되기 때문에 모든 명령이 커밋되거나 모든 명령이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-114">Because the commands in a transaction are managed as a unit, either all commands are committed, or all commands are rolled back.</span></span>

<span data-ttu-id="beb4a-115">트랜잭션은 데이터 처리에서 널리 사용 되며, 특히 데이터베이스 작업 및 금융 트랜잭션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-115">Transactions are widely used in data processing, most notably in database operations and for financial transactions.</span></span> <span data-ttu-id="beb4a-116">트랜잭션은 명령 집합에 대 한 최악의 시나리오에서 모두 실패 하는 것은 아니지만 일부 명령이 실패 하는 경우에는 복구 하기 어려운 손상 됨, 거짓 또는 중단 되지 않은 상태에서 시스템을 종료 하는 경우에 가장 자주 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-116">Transactions are most often used when the worst-case scenario for a set of commands is not that they all fail, but that some commands succeed while others fail, leaving the system in a damaged, false, or uninterpretable state that is difficult to repair.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="beb4a-117">트랜잭션 CMDLET</span><span class="sxs-lookup"><span data-stu-id="beb4a-117">TRANSACTION CMDLETS</span></span>

<span data-ttu-id="beb4a-118">PowerShell에는 트랜잭션 관리를 위해 설계 된 몇 가지 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-118">PowerShell includes several cmdlets designed for managing transactions.</span></span>

- <span data-ttu-id="beb4a-119">Start-Transaction: 새 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-119">Start-Transaction: Starts a new transaction.</span></span>
- <span data-ttu-id="beb4a-120">Use-Transaction: 트랜잭션에 명령 또는 식을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-120">Use-Transaction: Adds a command or expression to the transaction.</span></span> <span data-ttu-id="beb4a-121">명령은 트랜잭션 사용 개체를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-121">The command must use transaction-enabled objects.</span></span>
- <span data-ttu-id="beb4a-122">실행 취소-트랜잭션에 의해 데이터가 변경 되지 않도록 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-122">Undo-Transaction: Rolls back the transaction so that no data is changed by the transaction.</span></span>
- <span data-ttu-id="beb4a-123">Complete-Transaction: 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-123">Complete-Transaction: Commits the transaction.</span></span> <span data-ttu-id="beb4a-124">트랜잭션의 영향을 받는 데이터가 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-124">The data affected by the transaction is changed.</span></span>
- <span data-ttu-id="beb4a-125">Get Transaction: 활성 트랜잭션에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-125">Get-Transaction: Gets information about the active transaction.</span></span>

<span data-ttu-id="beb4a-126">트랜잭션 cmdlet 목록을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="beb4a-126">For a list of transaction cmdlets, type:</span></span>

```powershell
get-command *transaction
```

<span data-ttu-id="beb4a-127">Cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="beb4a-127">For detailed information about the cmdlets, type:</span></span>

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a><span data-ttu-id="beb4a-128">트랜잭션 사용 요소</span><span class="sxs-lookup"><span data-stu-id="beb4a-128">TRANSACTION-ENABLED ELEMENTS</span></span>

<span data-ttu-id="beb4a-129">트랜잭션에 참여 하려면 cmdlet과 공급자 모두 트랜잭션을 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-129">To participate in a transaction, both the cmdlet and the provider must support transactions.</span></span> <span data-ttu-id="beb4a-130">이 기능은 트랜잭션의 영향을 받는 개체에 기본 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-130">This feature is built in to the objects that are affected by the transaction.</span></span>

<span data-ttu-id="beb4a-131">PowerShell 레지스트리 공급자는 Windows Vista에서 트랜잭션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-131">The PowerShell Registry provider supports transactions in Windows Vista.</span></span> <span data-ttu-id="beb4a-132">TransactedString 개체 (TransactedString)는 PowerShell을 실행 하는 모든 운영 체제에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-132">The TransactedString object (Microsoft.PowerShell.Commands.Management.TransactedString) works with any operating system that runs PowerShell.</span></span>

<span data-ttu-id="beb4a-133">다른 PowerShell 공급자는 트랜잭션을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-133">Other PowerShell providers can support transactions.</span></span> <span data-ttu-id="beb4a-134">세션에서 트랜잭션을 지 원하는 PowerShell 공급자를 찾으려면 다음 명령을 사용 하 여 공급자의 기능 속성에서 "트랜잭션" 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-134">To find the PowerShell providers in your session that support transactions, use the following command to find the "Transactions" value in the Capabilities property of providers:</span></span>

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

<span data-ttu-id="beb4a-135">공급자에 대 한 자세한 내용은 공급자에 대 한 도움말을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="beb4a-135">For more information about a provider, see the Help for the provider.</span></span> <span data-ttu-id="beb4a-136">공급자 도움말을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-136">To get provider Help, type:</span></span>

```
get-help <provider-name>
```

<span data-ttu-id="beb4a-137">예를 들어 레지스트리 공급자에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-137">For example, to get Help for the Registry provider, type:</span></span>

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a><span data-ttu-id="beb4a-138">USETRANSACTION 매개 변수</span><span class="sxs-lookup"><span data-stu-id="beb4a-138">THE USETRANSACTION PARAMETER</span></span>

<span data-ttu-id="beb4a-139">트랜잭션을 지원할 수 있는 cmdlet에는 UseTransaction 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-139">Cmdlets that can support transactions have a UseTransaction parameter.</span></span> <span data-ttu-id="beb4a-140">이 매개 변수는 활성 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-140">This parameter includes the command in the active transaction.</span></span> <span data-ttu-id="beb4a-141">전체 매개 변수 이름 또는 해당 별칭 ("usetx")을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-141">You can use the full parameter name or its alias, "usetx".</span></span>

<span data-ttu-id="beb4a-142">매개 변수는 세션이 활성 트랜잭션을 포함 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-142">The parameter can be used only when the session contains an active transaction.</span></span> <span data-ttu-id="beb4a-143">활성 트랜잭션이 없을 때 UseTransaction 매개 변수를 사용 하 여 명령을 입력 하면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-143">If you enter a command with the UseTransaction parameter when there is no active transaction, the command fails.</span></span>

<span data-ttu-id="beb4a-144">UseTransaction 매개 변수를 사용 하 여 cmdlet을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-144">To find cmdlets with the UseTransaction parameter, type:</span></span>

```powershell
get-help * -parameter UseTransaction
```

<span data-ttu-id="beb4a-145">PowerShell core에서 PowerShell 공급자와 함께 작동 하도록 설계 된 모든 cmdlet은 트랜잭션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-145">In PowerShell core, all of the cmdlets designed to work with PowerShell providers support transactions.</span></span> <span data-ttu-id="beb4a-146">따라서 공급자 cmdlet을 사용 하 여 트랜잭션을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-146">As a result, you can use the provider cmdlets to manage transactions.</span></span>

<span data-ttu-id="beb4a-147">PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="beb4a-147">For more information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

## <a name="the-transaction-object"></a><span data-ttu-id="beb4a-148">트랜잭션 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-148">THE TRANSACTION OBJECT</span></span>

<span data-ttu-id="beb4a-149">트랜잭션은 PowerShell에서 트랜잭션 개체인 System.object로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-149">Transactions are represented in PowerShell by a transaction object, System.Management.Automation.Transaction.</span></span>

<span data-ttu-id="beb4a-150">개체에는 다음 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-150">The object has the following properties:</span></span>

- <span data-ttu-id="beb4a-151">RollbackPreference: 현재 트랜잭션에 대 한 롤백 기본 설정 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-151">RollbackPreference: Contains the rollback preference set for the current transaction.</span></span> <span data-ttu-id="beb4a-152">Start-Transaction를 사용 하 여 트랜잭션을 시작할 때 롤백 기본 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-152">You can set the rollback preference when you use Start-Transaction to start the transaction.</span></span>

  <span data-ttu-id="beb4a-153">Rollback 기본 설정에 따라 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-153">The rollback preference determines the conditions under which the transaction is rolled back automatically.</span></span> <span data-ttu-id="beb4a-154">유효한 값은 Error, TerminatingError 및 Never입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-154">Valid values are Error, TerminatingError, and Never.</span></span> <span data-ttu-id="beb4a-155">기본값은 Error입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-155">The default value is Error.</span></span>

- <span data-ttu-id="beb4a-156">상태: 트랜잭션의 현재 상태를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-156">Status: Contains the current status of the transaction.</span></span> <span data-ttu-id="beb4a-157">유효한 값은 활성, 커밋 및 RolledBack입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-157">Valid values are Active, Committed, and RolledBack.</span></span>

- <span data-ttu-id="beb4a-158">SubscriberCount: 트랜잭션에 대 한 구독자 수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-158">SubscriberCount: Contains the number of subscribers to the transaction.</span></span> <span data-ttu-id="beb4a-159">다른 트랜잭션이 진행 중인 동안에는 트랜잭션을 시작할 때 구독자가 트랜잭션에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-159">A subscriber is added to a transaction when you start a transaction while another transaction is in progress.</span></span> <span data-ttu-id="beb4a-160">구독자가 트랜잭션을 커밋하면 구독자 수가 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-160">The subscriber count is decremented when a subscriber commits the transaction.</span></span>

## <a name="active-transactions"></a><span data-ttu-id="beb4a-161">활성 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="beb4a-161">ACTIVE TRANSACTIONS</span></span>

<span data-ttu-id="beb4a-162">PowerShell에서는 한 번에 하나의 트랜잭션만 활성화 되며 활성 트랜잭션만 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-162">In PowerShell, only one transaction is active at a time, and you can manage only the active transaction.</span></span> <span data-ttu-id="beb4a-163">동시에 여러 트랜잭션이 동일한 세션에서 진행 될 수 있지만 가장 최근에 시작 된 트랜잭션만 활성 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-163">Multiple transactions can be in progress in the same session at the same time, but only the most-recently started transaction is active.</span></span>

<span data-ttu-id="beb4a-164">따라서 트랜잭션 cmdlet을 사용 하는 경우 특정 트랜잭션을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-164">As a result, you cannot specify a particular transaction when using the transaction cmdlets.</span></span> <span data-ttu-id="beb4a-165">명령은 항상 활성 트랜잭션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-165">Commands always apply to the active transaction.</span></span>

<span data-ttu-id="beb4a-166">이는 Get-Transaction cmdlet의 동작에서 가장 분명 하 게 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-166">This is most evident in the behavior of the Get-Transaction cmdlet.</span></span> <span data-ttu-id="beb4a-167">Get-Transaction 명령을 입력 하면 항상 하나의 트랜잭션 개체만 가져옵니다 Get-Transaction.</span><span class="sxs-lookup"><span data-stu-id="beb4a-167">When you enter a Get-Transaction command, Get-Transaction always gets only one transaction object.</span></span> <span data-ttu-id="beb4a-168">이 개체는 활성 트랜잭션을 나타내는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-168">This object is the object that represents the active transaction.</span></span>

<span data-ttu-id="beb4a-169">다른 트랜잭션을 관리 하려면 먼저 해당 트랜잭션을 커밋하거나 롤백하여 활성 트랜잭션을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-169">To manage a different transaction, you must first finish the active transaction, either by committing it or rolling it back.</span></span> <span data-ttu-id="beb4a-170">이렇게 하면 이전 트랜잭션이 자동으로 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-170">When you do this, the previous transaction becomes active automatically.</span></span> <span data-ttu-id="beb4a-171">트랜잭션은 시작 된 순서와 반대로 활성화 되므로 가장 최근에 시작 된 트랜잭션이 항상 활성 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-171">Transactions become active in the reverse of order of which they are started, so that the most recently started transaction is always active.</span></span>

## <a name="subscribers-and-independent-transactions"></a><span data-ttu-id="beb4a-172">구독자 및 독립 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="beb4a-172">SUBSCRIBERS AND INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="beb4a-173">다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작 하면 기본적으로 PowerShell에서 새 트랜잭션을 시작 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-173">If you start a transaction while another transaction is in progress, by default, PowerShell does not start a new transaction.</span></span> <span data-ttu-id="beb4a-174">대신 "구독자"를 현재 트랜잭션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-174">Instead, it adds a "subscriber" to the current transaction.</span></span>

<span data-ttu-id="beb4a-175">트랜잭션에 여러 구독자가 있는 경우 모든 시점에서 단일 Undo-Transaction 명령은 모든 구독자에 대 한 전체 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-175">When a transaction has multiple subscribers, a single Undo-Transaction command at any point rolls back the entire transaction for all subscribers.</span></span> <span data-ttu-id="beb4a-176">그러나 트랜잭션을 커밋하려면 모든 구독자에 대해 Complete-Transaction 명령을 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-176">However, to commit the transaction, you must enter a Complete-Transaction command for every subscriber.</span></span>

<span data-ttu-id="beb4a-177">트랜잭션에 대 한 구독자 수를 찾으려면 트랜잭션 개체의 SubscriberCount 속성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-177">To find the number of subscribers to a transaction, check the SubscriberCount property of the transaction object.</span></span> <span data-ttu-id="beb4a-178">예를 들어 다음 명령은 Get-Transaction cmdlet을 사용 하 여 활성 트랜잭션의 SubscriberCount 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-178">For example, the following command uses the Get-Transaction cmdlet to get the value of the SubscriberCount property of the active transaction:</span></span>

```powershell
(Get-Transaction).SubscriberCount
```

<span data-ttu-id="beb4a-179">다른 트랜잭션이 진행 되는 동안 시작 된 대부분의 트랜잭션이 원래 트랜잭션과 관련 되기 때문에 구독자를 추가 하는 것이 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-179">Adding a subscriber is the default behavior because most transactions that are started while another transaction is in progress are related to the original transaction.</span></span> <span data-ttu-id="beb4a-180">일반적인 모델에서 트랜잭션이 포함 된 스크립트는 자체 트랜잭션을 포함 하는 도우미 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-180">In the typical model, a script that contains a transaction calls a helper script that contains its own transaction.</span></span> <span data-ttu-id="beb4a-181">트랜잭션은 관련 되어 있으므로 하나의 단위로 롤백하거나 커밋해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-181">Because the transactions are related, they should be rolled back or committed as a unit.</span></span>

<span data-ttu-id="beb4a-182">그러나 Start-Transaction cmdlet의 독립 매개 변수를 사용 하 여 현재 트랜잭션과 독립적인 트랜잭션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-182">However, you can start a transaction that is independent of the current transaction by using the Independent parameter of the Start-Transaction cmdlet.</span></span>

<span data-ttu-id="beb4a-183">독립 트랜잭션을 시작 하면 Start-Transaction 새 트랜잭션 개체를 만들고 새 트랜잭션이 활성 트랜잭션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-183">When you start an independent transaction, Start-Transaction creates a new transaction object, and the new transaction becomes the active transaction.</span></span>
<span data-ttu-id="beb4a-184">원본 트랜잭션에 영향을 주지 않고 독립 트랜잭션을 커밋하거나 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-184">The independent transaction can be committed or rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="beb4a-185">독립 트랜잭션이 완료 (커밋 또는 롤백) 되 면 원래 트랜잭션은 다시 활성 트랜잭션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-185">When the independent transaction is finished (committed or rolled back), the original transaction becomes the active transaction again.</span></span>

## <a name="changing-data"></a><span data-ttu-id="beb4a-186">데이터 변경</span><span class="sxs-lookup"><span data-stu-id="beb4a-186">CHANGING DATA</span></span>

<span data-ttu-id="beb4a-187">트랜잭션을 사용 하 여 데이터를 변경 하는 경우 트랜잭션에 의해 영향을 받는 데이터는 트랜잭션을 커밋할 때까지 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-187">When you use transactions to change data, the data that is affected by the transaction is not changed until you commit the transaction.</span></span> <span data-ttu-id="beb4a-188">그러나 트랜잭션의 일부가 아닌 명령으로 동일한 데이터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-188">However, the same data can be changed by commands that are not part of the transaction.</span></span>

<span data-ttu-id="beb4a-189">트랜잭션을 사용 하 여 공유 데이터를 관리 하는 경우이 점을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-189">Keep this in mind when you are using transactions to manage shared data.</span></span>
<span data-ttu-id="beb4a-190">일반적으로 데이터베이스에는 작업 하는 동안 데이터를 잠그는 메커니즘이 있습니다 .이 메커니즘을 사용 하면 다른 사용자 및 다른 명령, 스크립트 및 함수를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-190">Typically, databases have mechanisms that lock the data while you are working on it, preventing other users, and other commands, scripts, and functions, from changing it.</span></span>

<span data-ttu-id="beb4a-191">그러나 잠금은 데이터베이스의 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-191">However, the lock is a feature of the database.</span></span> <span data-ttu-id="beb4a-192">트랜잭션과는 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-192">It is not related to transactions.</span></span> <span data-ttu-id="beb4a-193">트랜잭션 사용 파일 시스템이 나 다른 데이터 저장소에서 작업 하는 경우 트랜잭션이 진행 되는 동안 데이터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-193">If you are working in a transaction-enabled file system or other data store, the data can be changed while the transaction is in progress.</span></span>

## <a name="examples"></a><span data-ttu-id="beb4a-194">예제</span><span class="sxs-lookup"><span data-stu-id="beb4a-194">EXAMPLES</span></span>

<span data-ttu-id="beb4a-195">이 섹션의 예제에서는 PowerShell 레지스트리 공급자를 사용 하며 사용자가 잘 알고 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-195">The examples in this section use the PowerShell Registry provider and assume that you are familiar with it.</span></span> <span data-ttu-id="beb4a-196">레지스트리 공급자에 대 한 자세한 내용을 보려면 "get-help Registry"를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="beb4a-196">For information about the Registry provider, type "get-help registry".</span></span>

### <a name="example-1-committing-a-transaction"></a><span data-ttu-id="beb4a-197">예 1: 트랜잭션 커밋</span><span class="sxs-lookup"><span data-stu-id="beb4a-197">EXAMPLE 1: COMMITTING A TRANSACTION</span></span>

<span data-ttu-id="beb4a-198">트랜잭션을 만들려면 Start-Transaction cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-198">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="beb4a-199">다음 명령은 기본 설정을 사용 하 여 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-199">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-200">트랜잭션에 명령을 포함 하려면 cmdlet의 UseTransaction 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-200">To include commands in the transaction, use the UseTransaction parameter of the cmdlet.</span></span> <span data-ttu-id="beb4a-201">기본적으로 명령은 트랜잭션에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-201">By default, commands are not included in the transaction,</span></span>

<span data-ttu-id="beb4a-202">예를 들어 HKCU: 드라이브의 소프트웨어 키에서 현재 위치를 설정 하는 다음 명령은 트랜잭션에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-202">For example, the following command, which sets the current location in the Software key of the HKCU: drive, is not included in the transaction.</span></span>

```powershell
cd hkcu:\Software
```

<span data-ttu-id="beb4a-203">MyCompany 키를 만드는 다음 명령은 New-Item cmdlet의 UseTransaction 매개 변수를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-203">The following command, which creates the MyCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="beb4a-204">이 명령은 새 키를 나타내는 개체를 반환 하지만, 명령이 트랜잭션의 일부 이므로 레지스트리가 아직 변경 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-204">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

<span data-ttu-id="beb4a-205">트랜잭션을 커밋하려면 Complete-Transaction cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-205">To commit the transaction, use the Complete-Transaction cmdlet.</span></span> <span data-ttu-id="beb4a-206">항상 활성 트랜잭션에 영향을 주므로 트랜잭션을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-206">Because it always affects the active transaction, you cannot specify the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="beb4a-207">따라서 MyCompany 키가 레지스트리에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-207">As a result, the MyCompany key is added to the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a><span data-ttu-id="beb4a-208">예 2: 트랜잭션 롤백</span><span class="sxs-lookup"><span data-stu-id="beb4a-208">EXAMPLE 2: ROLLING BACK A TRANSACTION</span></span>

<span data-ttu-id="beb4a-209">트랜잭션을 만들려면 Start-Transaction cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-209">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="beb4a-210">다음 명령은 기본 설정을 사용 하 여 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-210">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-211">MyOtherCompany 키를 만드는 다음 명령은 New-Item cmdlet의 UseTransaction 매개 변수를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-211">The following command, which creates the MyOtherCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -UseTransaction
```

<span data-ttu-id="beb4a-212">이 명령은 새 키를 나타내는 개체를 반환 하지만, 명령이 트랜잭션의 일부 이므로 레지스트리가 아직 변경 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-212">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

<span data-ttu-id="beb4a-213">트랜잭션을 롤백하려면 Undo-Transaction cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-213">To roll back the transaction, use the Undo-Transaction cmdlet.</span></span> <span data-ttu-id="beb4a-214">항상 활성 트랜잭션에 영향을 주므로 트랜잭션을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-214">Because it always affects the active transaction, you do not specify the transaction.</span></span>

```powershell
Undo-transaction
```

<span data-ttu-id="beb4a-215">그러면 MyOtherCompany 키가 레지스트리에 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-215">The result is that the MyOtherCompany key is not added to the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a><span data-ttu-id="beb4a-216">예 3: 트랜잭션 미리 보기</span><span class="sxs-lookup"><span data-stu-id="beb4a-216">EXAMPLE 3: PREVIEWING A TRANSACTION</span></span>

<span data-ttu-id="beb4a-217">일반적으로 트랜잭션 변경 데이터에 사용 되는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-217">Typically, the commands used in a transaction change data.</span></span> <span data-ttu-id="beb4a-218">그러나 데이터를 가져오는 명령은 트랜잭션 내에서 데이터를 가져오기 때문에 트랜잭션 에서도 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-218">However, the commands that get data are useful in a transaction, too, because they get data inside of the transaction.</span></span> <span data-ttu-id="beb4a-219">이렇게 하면 트랜잭션을 커밋하는 변경 내용에 대 한 미리 보기가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-219">This provides a preview of the changes that committing the transaction would cause.</span></span>

<span data-ttu-id="beb4a-220">다음 예에서는 Get-ChildItem 명령을 사용 하는 방법을 보여 줍니다. 별칭은 "dir"을 사용 하 여 트랜잭션의 변경 내용을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-220">The following example shows how to use the Get-ChildItem command (the alias is "dir") to preview the changes in a transaction.</span></span>

<span data-ttu-id="beb4a-221">다음 명령은 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-221">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-222">다음 명령은 New-ItemProperty cmdlet을 사용 하 여 MyCompany 키에 MyKey 레지스트리 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-222">The following command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="beb4a-223">이 명령은 UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-223">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

<span data-ttu-id="beb4a-224">이 명령은 새 레지스트리 항목을 나타내는 개체를 반환 하지만 레지스트리 항목은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-224">The command returns an object representing the new registry entry, but the registry entry is not changed.</span></span>

```
MyKey
-----
123
```

<span data-ttu-id="beb4a-225">현재 레지스트리에 있는 항목을 가져오려면 UseTransaction 매개 변수 없이 Get-ChildItem 명령 ("dir")을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-225">To get the items that are currently in the registry, use a Get-ChildItem command ("dir") without the UseTransaction parameter.</span></span> <span data-ttu-id="beb4a-226">다음 명령은 "M"으로 시작 하는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-226">The following command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="beb4a-227">결과는 아직 MyCompany 키에 추가 된 항목이 없음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-227">The result shows that no entries have yet been added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

<span data-ttu-id="beb4a-228">트랜잭션 커밋의 효과를 미리 보려면 UseTransaction 매개 변수를 사용 하 여 Get-ChildItem ("dir") 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-228">To preview the effect of committing the transaction, enter a Get-ChildItem ("dir") command with the UseTransaction parameter.</span></span> <span data-ttu-id="beb4a-229">이 명령에는 트랜잭션 내의 데이터 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-229">This command has a view of the data from within the transaction.</span></span>

```powershell
dir m* -useTransaction
```

<span data-ttu-id="beb4a-230">결과가 표시 되 면 트랜잭션이 커밋되면 MyKey 항목이 MyCompany 키에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-230">The result shows that, if the transaction is committed, the MyKey entry will be added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a><span data-ttu-id="beb4a-231">예제 4: 트랜잭션 및 비트랜잭션 명령 결합</span><span class="sxs-lookup"><span data-stu-id="beb4a-231">EXAMPLE 4: COMBINING TRANSACTED AND NON-TRANSACTED COMMANDS</span></span>

<span data-ttu-id="beb4a-232">트랜잭션 중에 비트랜잭션 명령을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-232">You can enter non-transacted commands during a transaction.</span></span> <span data-ttu-id="beb4a-233">비트랜잭션 명령은 데이터에 즉시 영향을 주지만 트랜잭션에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-233">The non-transacted commands affect the data immediately, but they do not affect the transaction.</span></span>
<span data-ttu-id="beb4a-234">다음 명령은 HKCU: \ Software 레지스트리 키에서 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-234">The following command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-235">다음 세 명령은 New-Item cmdlet을 사용 하 여 레지스트리에 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-235">The next three commands use the New-Item cmdlet to add keys to the registry.</span></span>
<span data-ttu-id="beb4a-236">첫 번째 및 세 번째 명령은 UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-236">The first and third commands use the UseTransaction parameter to include the commands in the transaction.</span></span> <span data-ttu-id="beb4a-237">두 번째 명령은 매개 변수를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-237">The second command omits the parameter.</span></span> <span data-ttu-id="beb4a-238">두 번째 명령이 트랜잭션에 포함 되지 않기 때문에 즉시 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-238">Because the second command is not included in the transaction, it is effective immediately.</span></span>

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

<span data-ttu-id="beb4a-239">레지스트리의 현재 상태를 보려면 UseTransaction 매개 변수 없이 Get-ChildItem ("dir") 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-239">To view the current state of the registry, use a Get-ChildItem ("dir") command without the UseTransaction parameter.</span></span> <span data-ttu-id="beb4a-240">이 명령은 "M"으로 시작 하는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-240">This command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="beb4a-241">결과는 MyCompany2 키가 레지스트리에 추가 되었음을 보여 주지만 트랜잭션의 일부인 MyCompany1 및 MyCompany3 키는 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-241">The result shows that the MyCompany2 key is added to the registry, but the MyCompany1 and MyCompany3 keys, which are part of the transaction, are not added.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

<span data-ttu-id="beb4a-242">다음 명령은 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-242">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="beb4a-243">이제 트랜잭션의 일부로 추가 된 키가 레지스트리에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-243">Now, the keys that were added as part of the transaction appear in the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a><span data-ttu-id="beb4a-244">예 5: 자동 롤백 사용</span><span class="sxs-lookup"><span data-stu-id="beb4a-244">EXAMPLE 5: USING AUTOMATIC ROLLBACK</span></span>

<span data-ttu-id="beb4a-245">트랜잭션의 명령이 어떤 종류의 오류를 생성 하는 경우 트랜잭션이 자동으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-245">When a command in a transaction generates an error of any kind, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="beb4a-246">이 기본 동작은 트랜잭션을 실행 하는 스크립트를 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-246">This default behavior is designed for scripts that run transactions.</span></span> <span data-ttu-id="beb4a-247">스크립트는 일반적으로 잘 테스트 되 고 오류 처리 논리를 포함 하므로 오류가 예상 되지 않으며 트랜잭션을 종료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-247">Scripts are typically well tested and include error-handling logic, so errors are not expected and should terminate the transaction.</span></span>

<span data-ttu-id="beb4a-248">첫 번째 명령은 HKCU: \ Software 레지스트리 키에서 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-248">The first command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-249">다음 명령은 New-Item cmdlet을 사용 하 여 MyCompany 키를 레지스트리에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-249">The following command uses the New-Item cmdlet to add the MyCompany key to the registry.</span></span> <span data-ttu-id="beb4a-250">이 명령은 UseTransaction 매개 변수를 사용 하 여 (별칭은 "usetx") 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-250">The command uses the UseTransaction parameter (the alias is "usetx") to include the command in the transaction.</span></span>

```powershell
New-Item MyCompany -UseTX
```

<span data-ttu-id="beb4a-251">MyCompany 키가 레지스트리에 이미 존재 하기 때문에 명령이 실패 하 고 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-251">Because the MyCompany key already exists in the registry, the command fails, and the transaction is rolled back.</span></span>

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="beb4a-252">Get-Transaction 명령은 트랜잭션이 롤백되고 SubscriberCount가 0 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-252">A Get-Transaction command confirms that the transaction has been rolled back and that the SubscriberCount is 0.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a><span data-ttu-id="beb4a-253">예 6: 롤백 기본 설정 변경</span><span class="sxs-lookup"><span data-stu-id="beb4a-253">EXAMPLE 6: CHANGING THE ROLLBACK PREFERENCE</span></span>

<span data-ttu-id="beb4a-254">트랜잭션을 더 이상 오류를 허용 하려면 Start-Transaction의 RollbackPreference 매개 변수를 사용 하 여 기본 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-254">If you want the transaction to be more error tolerant, you can use the RollbackPreference parameter of Start-Transaction to change the preference.</span></span>

<span data-ttu-id="beb4a-255">다음 명령은 rollback 기본 설정인 "Never"를 사용 하 여 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-255">The following command starts a transaction with a rollback preference of "Never".</span></span>

```powershell
start-transaction -rollbackpreference Never
```

<span data-ttu-id="beb4a-256">이 경우 명령이 실패 하면 트랜잭션이 자동으로 롤백되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-256">In this case, when the command fails, the transaction is not automatically rolled back.</span></span>

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="beb4a-257">트랜잭션이 아직 활성 상태 이므로 트랜잭션의 일부로 명령을 다시 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-257">Because the transaction is still active, you can resubmit the command as part of the transaction.</span></span>

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a><span data-ttu-id="beb4a-258">예 7: USE-TRANSACTION CMDLET 사용</span><span class="sxs-lookup"><span data-stu-id="beb4a-258">EXAMPLE 7: USING THE USE-TRANSACTION CMDLET</span></span>

<span data-ttu-id="beb4a-259">Use-Transaction cmdlet을 사용 하면 트랜잭션 사용 Microsoft .NET Framework 개체에 대해 직접 스크립팅을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-259">The Use-Transaction cmdlet enables you to do direct scripting against transaction-enabled Microsoft .NET Framework objects.</span></span> <span data-ttu-id="beb4a-260">Use-Transaction은 TransactedString 클래스의 인스턴스와 같이 트랜잭션 사용 .NET Framework 개체를 사용 하는 명령 및 식만 포함할 수 있는 스크립트 블록을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-260">Use-Transaction takes a script block that can only contain commands and expressions that use transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="beb4a-261">다음 명령은 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-261">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-262">다음 New-Object 명령은 TransactedString 클래스의 인스턴스를 만들어 $t 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-262">The following New-Object command creates an instance of the TransactedString class and saves it in the $t variable.</span></span>

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

<span data-ttu-id="beb4a-263">다음 명령은 TransactedString 개체의 Append 메서드를 사용 하 여 문자열에 텍스트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-263">The following command uses the Append method of the TransactedString object to add text to the string.</span></span> <span data-ttu-id="beb4a-264">이 명령은 트랜잭션의 일부가 아니므로 변경 내용이 즉시 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-264">Because the command is not part of the transaction, the change is effective immediately.</span></span>

```powershell
$t.append("Windows")
```

<span data-ttu-id="beb4a-265">다음 명령은 동일한 Append 메서드를 사용 하 여 텍스트를 추가 하지만 트랜잭션 일부로 텍스트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-265">The following command uses the same Append method to add text, but it adds the text as part of the transaction.</span></span> <span data-ttu-id="beb4a-266">명령은 중괄호로 묶이고 Use-Transaction의 ScriptBlock 매개 변수 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-266">The command is enclosed in braces, and it is set as the value of the ScriptBlock parameter of Use-Transaction.</span></span> <span data-ttu-id="beb4a-267">UseTransaction 매개 변수 (UseTx)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-267">The UseTransaction parameter (UseTx) is required.</span></span>

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

<span data-ttu-id="beb4a-268">$T에서 트랜잭션 문자열의 현재 내용을 보려면 TransactedString 개체의 ToString 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-268">To see the current content of the transacted string in $t, use the ToString method of the TransactedString object.</span></span>

```powershell
$t.tostring()
```

<span data-ttu-id="beb4a-269">출력에는 비트랜잭션 변경 내용만 적용 됨이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-269">The output shows that only the non-transacted changes are effective.</span></span>

```output
Windows
```

<span data-ttu-id="beb4a-270">트랜잭션 내에서 $t 트랜잭션 문자열의 현재 내용을 보려면 Use-Transaction 명령에 식을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-270">To see the current content of the transacted string in $t from within the transaction, embed the expression in a Use-Transaction command.</span></span>

```powershell
use-transaction {$s.tostring()} -usetx
```

<span data-ttu-id="beb4a-271">출력은 트랜잭션 뷰를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-271">The output shows the transaction view.</span></span>

```output
PowerShell
```

<span data-ttu-id="beb4a-272">다음 명령은 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-272">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="beb4a-273">최종 문자열을 보려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-273">To see the final string:</span></span>

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a><span data-ttu-id="beb4a-274">예 8: 다중 구독자 트랜잭션 관리</span><span class="sxs-lookup"><span data-stu-id="beb4a-274">EXAMPLE 8: MANAGING MULTI-SUBSCRIBER TRANSACTIONS</span></span>

<span data-ttu-id="beb4a-275">다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작할 때 PowerShell은 기본적으로 두 번째 트랜잭션을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-275">When you start a transaction while another transaction is in progress, PowerShell does not create a second transaction by default.</span></span> <span data-ttu-id="beb4a-276">대신 현재 트랜잭션에 구독자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-276">Instead, it adds a subscriber to the current transaction.</span></span>

<span data-ttu-id="beb4a-277">이 예에서는 다중 구독자 트랜잭션을 보고 관리 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-277">This example shows how to view and manage a multi-subscriber transaction.</span></span>

<span data-ttu-id="beb4a-278">먼저 HKCU: \ Software 키에서 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-278">Begin by starting a transaction in the HKCU:\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-279">다음 명령은 Get-Transaction 명령을 사용 하 여 활성 트랜잭션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-279">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="beb4a-280">결과는 활성 트랜잭션을 나타내는 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-280">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="beb4a-281">다음 명령은 레지스트리에 MyCompany 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-281">The following command adds the MyCompany key to the registry.</span></span> <span data-ttu-id="beb4a-282">이 명령은 UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-282">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="beb4a-283">다음 명령은 Start-Transaction 명령을 사용 하 여 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-283">The following command uses the Start-Transaction command to start a transaction.</span></span> <span data-ttu-id="beb4a-284">명령 프롬프트에서이 명령을 입력 하는 경우에도이 시나리오는 트랜잭션이 포함 된 스크립트를 실행할 때 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-284">Although this command is typed at the command prompt, this scenario is more likely to happen when you run a script that contains a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-285">Get-Transaction 명령은 트랜잭션 개체의 구독자 수가 증가 하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-285">A Get-Transaction command shows that the subscriber count on the transaction object is incremented.</span></span> <span data-ttu-id="beb4a-286">값은 이제 2입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-286">The value is now 2.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="beb4a-287">다음 명령은 New-ItemProperty cmdlet을 사용 하 여 MyCompany 키에 MyKey 레지스트리 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-287">The next command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="beb4a-288">UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-288">It uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

<span data-ttu-id="beb4a-289">MyCompany 키가 레지스트리에 없지만이 명령은 두 명령이 동일한 트랜잭션에 포함 되어 있기 때문에 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-289">The MyCompany key does not exist in the registry, but this command succeeds because the two commands are part of the same transaction.</span></span>

<span data-ttu-id="beb4a-290">다음 명령은 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-290">The following command commits the transaction.</span></span> <span data-ttu-id="beb4a-291">트랜잭션을 롤백하는 경우 모든 구독자에 대해 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-291">If it rolled back the transaction, the transaction would be rolled back for all the subscribers.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="beb4a-292">Get-Transaction 명령은 트랜잭션 개체의 구독자 수가 1 이지만 Status 값이 아직 활성 (커밋되지 않음) 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-292">A Get-Transaction command shows that the subscriber count on the transaction object is 1, but the value of Status is still Active (not Committed).</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="beb4a-293">트랜잭션 커밋을 완료 하려면 두 번째 Complete Transaction 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-293">To finish committing the transaction, enter a second Complete- Transaction command.</span></span> <span data-ttu-id="beb4a-294">다중 구독자 트랜잭션을 커밋하려면 각 Start-Transaction 명령에 대해 하나의 Complete-Transaction 명령을 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-294">To commit a multi-subscriber transaction, you must enter one Complete-Transaction command for each Start-Transaction command.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="beb4a-295">다른 Get-Transaction 명령은 트랜잭션이 커밋 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-295">Another Get-Transaction command shows that the transaction has been committed.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a><span data-ttu-id="beb4a-296">예 9: 독립 트랜잭션 관리</span><span class="sxs-lookup"><span data-stu-id="beb4a-296">EXAMPLE 9: MANAGING INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="beb4a-297">다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작할 때 Start-Transaction의 독립적인 매개 변수를 사용 하 여 새 트랜잭션을 원래 트랜잭션과 독립적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-297">When you start a transaction while another transaction is in progress, you can use the Independent parameter of Start-Transaction to make the new transaction independent of the original transaction.</span></span>

<span data-ttu-id="beb4a-298">이렇게 하면 Start-Transaction 새 트랜잭션 개체를 만들고 새 트랜잭션을 활성 트랜잭션으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-298">When you do, Start-Transaction creates a new transaction object and makes the new transaction the active transaction.</span></span>

<span data-ttu-id="beb4a-299">먼저 HKCU: Software 키에서 트랜잭션을 시작 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-299">Begin by starting a transaction in the HKCU:\\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="beb4a-300">다음 명령은 Get-Transaction 명령을 사용 하 여 활성 트랜잭션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-300">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="beb4a-301">결과는 활성 트랜잭션을 나타내는 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-301">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="beb4a-302">다음 명령은 트랜잭션의 일부로 MyCompany 레지스트리 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-302">The following command adds the MyCompany registry key as part of the transaction.</span></span> <span data-ttu-id="beb4a-303">UseTransaction 매개 변수 (UseTx)를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-303">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -use
```

<span data-ttu-id="beb4a-304">다음 명령은 새 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-304">The following command starts a new transaction.</span></span> <span data-ttu-id="beb4a-305">이 명령은 독립 매개 변수를 사용 하 여이 트랜잭션이 활성 트랜잭션에 대 한 구독자가 아님을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-305">The command uses the Independent parameter to indicate that this transaction is not a subscriber to the active transaction.</span></span>

```powershell
start-transaction -independent
```

<span data-ttu-id="beb4a-306">독립 트랜잭션을 만들 때 새로운 (가장 최근에 생성 된) 트랜잭션이 활성 트랜잭션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-306">When you create an independent transaction, the new (most-recently created) transaction becomes the active transaction.</span></span> <span data-ttu-id="beb4a-307">Get-Transaction 명령을 사용 하 여 활성 트랜잭션을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-307">You can use a Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="beb4a-308">트랜잭션의 SubscriberCount는 1로, 다른 구독자가 없고 트랜잭션이 새로운 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-308">Note that the SubscriberCount of the transaction is 1, indicating that there are no other subscribers and that the transaction is new.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="beb4a-309">원본 트랜잭션을 관리 하려면 먼저 새 트랜잭션을 완료 (커밋 또는 롤백) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-309">The new transaction must be finished (either committed or rolled back) before you can manage the original transaction.</span></span>

<span data-ttu-id="beb4a-310">다음 명령은 MyOtherCompany 키를 레지스트리에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-310">The following command adds the MyOtherCompany key to the registry.</span></span> <span data-ttu-id="beb4a-311">UseTransaction 매개 변수 (UseTx)를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-311">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -usetx
```

<span data-ttu-id="beb4a-312">이제 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-312">Now, roll back the transaction.</span></span> <span data-ttu-id="beb4a-313">두 개의 구독자가 있는 단일 트랜잭션이 있는 경우 트랜잭션을 롤백하면 모든 구독자에 대 한 전체 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-313">If there were a single transaction with two subscribers, rolling back the transaction would roll back the entire transaction for all the subscribers.</span></span>

<span data-ttu-id="beb4a-314">그러나 이러한 트랜잭션은 독립적 이기 때문에 최신 트랜잭션을 롤백하여 레지스트리 변경 내용을 취소 하 고 원래 트랜잭션을 활성 트랜잭션으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-314">However, because these transactions are independent, rolling back the newest transaction cancels the registry changes and makes the original transaction the active transaction.</span></span>

```powershell
undo-transaction
```

<span data-ttu-id="beb4a-315">Get-Transaction 명령은 원본 트랜잭션이 세션에서 여전히 활성 상태임을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-315">A Get-Transaction command confirms that the original transaction is still active in the session.</span></span>

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="beb4a-316">다음 명령은 활성 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-316">The following command commits the active transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="beb4a-317">Get-ChildItem 명령은 레지스트리가 변경 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beb4a-317">A Get-ChildItem command shows that the registry has been changed.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a><span data-ttu-id="beb4a-318">참고 항목</span><span class="sxs-lookup"><span data-stu-id="beb4a-318">SEE ALSO</span></span>

[<span data-ttu-id="beb4a-319">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="beb4a-319">Start-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Start-Transaction)

[<span data-ttu-id="beb4a-320">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="beb4a-320">Get-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Get-Transaction)

[<span data-ttu-id="beb4a-321">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="beb4a-321">Complete-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[<span data-ttu-id="beb4a-322">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="beb4a-322">Undo-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[<span data-ttu-id="beb4a-323">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="beb4a-323">Use-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Use-Transaction)

[<span data-ttu-id="beb4a-324">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="beb4a-324">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[<span data-ttu-id="beb4a-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="beb4a-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[<span data-ttu-id="beb4a-326">about_Providers</span><span class="sxs-lookup"><span data-stu-id="beb4a-326">about_Providers</span></span>](about_Providers.md)
