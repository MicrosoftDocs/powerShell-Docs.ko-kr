---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214354"
---
# <span data-ttu-id="cf025-103">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf025-103">Use-Transaction</span></span>

## <span data-ttu-id="cf025-104">개요</span><span class="sxs-lookup"><span data-stu-id="cf025-104">SYNOPSIS</span></span>
<span data-ttu-id="cf025-105">스크립트 블록을 활성 트랜잭션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-105">Adds the script block to the active transaction.</span></span>

## <span data-ttu-id="cf025-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf025-106">SYNTAX</span></span>

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="cf025-107">설명</span><span class="sxs-lookup"><span data-stu-id="cf025-107">DESCRIPTION</span></span>
<span data-ttu-id="cf025-108">**Use-transaction** cmdlet은 활성 트랜잭션에 스크립트 블록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-108">The **Use-Transaction** cmdlet adds a script block to an active transaction.</span></span>
<span data-ttu-id="cf025-109">이렇게 하면 트랜잭션 사용 Microsoft .NET 프레임 워크 개체를 사용 하 여 트랜잭션 스크립팅 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-109">This enables you to do transacted scripting by using transaction-enabled Microsoft .NET Framework objects.</span></span>
<span data-ttu-id="cf025-110">이 스크립트 블록에는 Microsoft.PowerShell.Commands.Management.TransactedString 클래스 등 트랜잭션이 사용 가능한 .NET Framework 개체만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-110">The script block can contain only transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="cf025-111">이 cmdlet을 사용 하는 경우 대부분의 cmdlet에 대 한 옵션인 *UseTransaction* 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-111">The *UseTransaction* parameter, which is optional for most cmdlets, is required when you use this cmdlet.</span></span>

<span data-ttu-id="cf025-112">**Use-Transaction** 은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-112">**Use-Transaction** is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="cf025-113">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf025-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="cf025-114">예제</span><span class="sxs-lookup"><span data-stu-id="cf025-114">EXAMPLES</span></span>

### <span data-ttu-id="cf025-115">예제 1: 트랜잭션 사용 개체를 사용 하 여 스크립팅</span><span class="sxs-lookup"><span data-stu-id="cf025-115">Example 1: Script by using a transaction-enabled object</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

<span data-ttu-id="cf025-116">이 예에서는 transaction 사용 .NET Framework 개체에 대해 **스크립트를 사용 하 여** 스크립트를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-116">This example shows how to use **Use-Transaction** to script against a transaction-enabled .NET Framework object.</span></span>
<span data-ttu-id="cf025-117">이 경우 개체는 **TransactedString** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-117">In this case, the object is a **TransactedString** object.</span></span>

<span data-ttu-id="cf025-118">첫 번째 명령은 Start-Transaction cmdlet을 사용하여 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-118">The first command uses the Start-Transaction cmdlet to start a transaction.</span></span>

<span data-ttu-id="cf025-119">두 번째 명령은 New-Object 명령을 사용 하 여 **TransactedString** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-119">The second command uses the New-Object command to create a **TransactedString** object.</span></span>
<span data-ttu-id="cf025-120">개체를 $TransactedString 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-120">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="cf025-121">세 번째 및 네 번째 명령은 모두 **TransactedString** 개체의 **Append** 메서드를 사용 하 여 $TransactedString 값에 텍스트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-121">The third and fourth commands both use the **Append** method of the **TransactedString** object to add text to the value of $TransactedString.</span></span>
<span data-ttu-id="cf025-122">한 명령은 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-122">One command is part of the transaction.</span></span>
<span data-ttu-id="cf025-123">다른 명령은이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-123">The other command is not.</span></span>

<span data-ttu-id="cf025-124">세 번째 명령은 트랜잭션 문자열의 **Append** 메서드를 사용 하 여 $TransactedString 값에 Hello를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-124">The third command uses the **Append** method of the transacted string to add Hello to the value of $TransactedString.</span></span>
<span data-ttu-id="cf025-125">이 명령은 트랜잭션의 일부가 아니므로 변경 사항이 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-125">Because the command is not part of the transaction, the change is applied immediately.</span></span>

<span data-ttu-id="cf025-126">네 번째 명령은 **-transaction을 사용** 하 여 트랜잭션의 문자열에 텍스트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-126">The fourth command uses **Use-Transaction** to add text to the string in the transaction.</span></span>
<span data-ttu-id="cf025-127">이 명령은 **Append** 메서드를 사용 하 여 $TransactedString 값에 ", 세계"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-127">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>
<span data-ttu-id="cf025-128">명령은 중괄호 ()로 묶어 {} 스크립트 블록으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-128">The command is enclosed in braces ( {} ) to make it a script block.</span></span>
<span data-ttu-id="cf025-129">*UseTransaction* 매개 변수는이 명령에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-129">The *UseTransaction* parameter is required in this command.</span></span>

<span data-ttu-id="cf025-130">다섯 번째 및 여섯 번째 명령은 **TransactedString** 개체의 **ToString** 메서드를 사용 하 여 **TransactedString** 값을 문자열로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-130">The fifth and sixth commands use the **ToString** method of the **TransactedString** object to display the value of the **TransactedString** as a string.</span></span>
<span data-ttu-id="cf025-131">다시 한 가지 명령은 트랜잭션의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-131">Again, one command is part of the transaction.</span></span>
<span data-ttu-id="cf025-132">다른 트랜잭션은 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-132">The other transaction is not.</span></span>

<span data-ttu-id="cf025-133">다섯 번째 명령은 **ToString** 메서드를 사용 하 여 $TransactedString 변수의 현재 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-133">The fifth command uses the **ToString** method to display the current value of the $TransactedString variable.</span></span>
<span data-ttu-id="cf025-134">이 명령은 트랜잭션의 일부가 아니므로 문자열의 현재 상태만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-134">Because it is not part of the transaction, it displays only the current state of the string.</span></span>

<span data-ttu-id="cf025-135">여섯 번째 명령은 **Use-transaction** 을 사용 하 여 트랜잭션에서 동일한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-135">The sixth command uses **Use-Transaction** to run the same command in the transaction.</span></span>
<span data-ttu-id="cf025-136">이 명령은 트랜잭션의 일부 이므로 트랜잭션 변경 내용 미리 보기와 매우 유사 하 게 트랜잭션의 현재 문자열 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-136">Because the command is part of the transaction, it displays the current value of the string in the transaction, much like a preview of the transaction changes.</span></span>

<span data-ttu-id="cf025-137">일곱 번째 명령은 Complete-Transaction cmdlet을 사용하여 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-137">The seventh command uses the Complete-Transaction cmdlet to commit the transaction.</span></span>

<span data-ttu-id="cf025-138">마지막 명령은 **ToString** 메서드를 사용 하 여 변수의 결과 값을 문자열로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-138">The final command uses the **ToString** method to display the resulting value of the variable as a string.</span></span>

### <span data-ttu-id="cf025-139">예 2: 트랜잭션 롤백</span><span class="sxs-lookup"><span data-stu-id="cf025-139">Example 2: Roll back a transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

<span data-ttu-id="cf025-140">이 예에서는 **Use transaction** 명령을 포함 하는 트랜잭션을 롤백하는 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-140">This example shows the effect of rolling back a transaction that includes **Use-Transaction** commands.</span></span>
<span data-ttu-id="cf025-141">트랜잭션의 다른 명령과 마찬가지로, 트랜잭션을 롤백하면 변경 사항이 취소되고 데이터가 원래대로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-141">Like all commands in a transaction, when the transaction is rolled back, the transacted changes are discarded and the data is unchanged.</span></span>

<span data-ttu-id="cf025-142">첫 번째 명령은 **Start transaction** 을 사용 하 여 트랜잭션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-142">The first command uses **Start-Transaction** to start a transaction.</span></span>

<span data-ttu-id="cf025-143">두 번째 명령은 **TransactedString** 개체를 사용 하 여 **새** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-143">The second command uses **New-Object** to create a **TransactedString** object.</span></span>
<span data-ttu-id="cf025-144">개체를 $TransactedString 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-144">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="cf025-145">트랜잭션의 일부가 아닌 세 번째 명령은 **Append** 메서드를 사용 하 여 $TransactedString 값에 "Hello"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-145">The third command, which is not part of the transaction, uses the **Append** method to add "Hello" to the value of $TransactedString.</span></span>

<span data-ttu-id="cf025-146">네 번째 명령은 transaction을 **사용** 하 여 트랜잭션에서 **Append** 메서드를 사용 하는 다른 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-146">The fourth command uses **Use-Transaction** to run another command that uses the **Append** method in the transaction.</span></span>
<span data-ttu-id="cf025-147">이 명령은 **Append** 메서드를 사용 하 여 $TransactedString 값에 ", 세계"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-147">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>

<span data-ttu-id="cf025-148">다섯 번째 명령은 Undo-Transaction cmdlet을 사용하여 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-148">The fifth command uses the Undo-Transaction cmdlet to roll back the transaction.</span></span>
<span data-ttu-id="cf025-149">따라서 트랜잭션에서 수행 된 모든 명령이 되돌려집니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-149">As a result, all commands performed in the transaction are reversed.</span></span>

<span data-ttu-id="cf025-150">마지막 명령은 **ToString** 메서드를 사용 하 여 $TransactedString 결과 값을 문자열로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-150">The final command uses the **ToString** method to display the resulting value of $TransactedString as a string.</span></span>
<span data-ttu-id="cf025-151">결과는 트랜잭션 외부에서 수행 된 변경 내용만 개체에 적용 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-151">The results show that only the changes that were made outside the transaction were applied to the object.</span></span>

## <span data-ttu-id="cf025-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf025-152">PARAMETERS</span></span>

### <span data-ttu-id="cf025-153">-TransactedScript</span><span class="sxs-lookup"><span data-stu-id="cf025-153">-TransactedScript</span></span>
<span data-ttu-id="cf025-154">트랜잭션에서 실행되는 스크립트 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-154">Specifies the script block that is run in the transaction.</span></span>
<span data-ttu-id="cf025-155">유효한 스크립트 블록을 중괄호( { } )로 묶어 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-155">Enter any valid script block enclosed in braces ( { } ).</span></span>
<span data-ttu-id="cf025-156">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-156">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf025-157">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="cf025-157">-UseTransaction</span></span>
<span data-ttu-id="cf025-158">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-158">Includes the command in the active transaction.</span></span>
<span data-ttu-id="cf025-159">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-159">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="cf025-160">자세한 내용은 about_transactions를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf025-160">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf025-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf025-161">CommonParameters</span></span>
<span data-ttu-id="cf025-162">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cf025-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf025-163">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf025-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf025-164">입력</span><span class="sxs-lookup"><span data-stu-id="cf025-164">INPUTS</span></span>

### <span data-ttu-id="cf025-165">없음</span><span class="sxs-lookup"><span data-stu-id="cf025-165">None</span></span>
<span data-ttu-id="cf025-166">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cf025-167">출력</span><span class="sxs-lookup"><span data-stu-id="cf025-167">OUTPUTS</span></span>

### <span data-ttu-id="cf025-168">PSObject</span><span class="sxs-lookup"><span data-stu-id="cf025-168">PSObject</span></span>
<span data-ttu-id="cf025-169">이 cmdlet은 트랜잭션 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-169">This cmdlet returns the result of the transaction.</span></span>

## <span data-ttu-id="cf025-170">참고</span><span class="sxs-lookup"><span data-stu-id="cf025-170">NOTES</span></span>

* <span data-ttu-id="cf025-171">*UseTransaction* 매개 변수는 활성 트랜잭션에 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-171">The *UseTransaction* parameter includes the command in the active transaction.</span></span> <span data-ttu-id="cf025-172">**Transaction** cmdlet은 항상 트랜잭션에서 사용 되기 때문에이 매개 변수는 사용 하는 **트랜잭션** 명령을 효과적으로 만드는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf025-172">Because the **Use-Transaction** cmdlet is always used in transactions, this parameter is required to make any **Use-Transaction** command effective.</span></span>

*

## <span data-ttu-id="cf025-173">관련 링크</span><span class="sxs-lookup"><span data-stu-id="cf025-173">RELATED LINKS</span></span>

[<span data-ttu-id="cf025-174">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf025-174">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="cf025-175">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf025-175">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="cf025-176">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf025-176">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="cf025-177">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf025-177">Undo-Transaction</span></span>](Undo-Transaction.md)
