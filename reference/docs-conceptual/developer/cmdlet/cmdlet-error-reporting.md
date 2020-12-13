---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 오류 보고
description: Cmdlet 오류 보고
ms.openlocfilehash: f06cf98183d56249080623895bd1f5a3e070cefd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653408"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="e793d-103">Cmdlet 오류 보고</span><span class="sxs-lookup"><span data-stu-id="e793d-103">Cmdlet error reporting</span></span>

<span data-ttu-id="e793d-104">Cmdlet은 오류 종료 오류 또는 종료 되지 않는 오류에 따라 오류를 다르게 보고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-104">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="e793d-105">종료 오류는 파이프라인이 즉시 종료 되도록 하는 오류 또는 처리를 계속할 이유가 없을 때 발생 하는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-105">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there's no reason to continue processing.</span></span> <span data-ttu-id="e793d-106">종료 되지 않는 오류는 현재 오류 조건을 보고 하는 오류 이지만 cmdlet은 입력 개체를 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-106">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="e793d-107">종료 되지 않는 오류가 발생 하면 일반적으로 사용자에 게 문제에 대 한 알림이 표시 되지만이 cmdlet은 다음 입력 개체를 계속 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-107">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="e793d-108">종료 및 비 종료 오류</span><span class="sxs-lookup"><span data-stu-id="e793d-108">Terminating and nonterminating errors</span></span>

<span data-ttu-id="e793d-109">다음 지침을 사용 하 여 오류 조건이 종료 오류 인지 아니면 종료 되지 않는 오류 인지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-109">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="e793d-110">오류 조건으로 인해 cmdlet이 더 이상 입력 개체를 성공적으로 처리 하지 못하는 경우</span><span class="sxs-lookup"><span data-stu-id="e793d-110">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="e793d-111">그렇다면 종료 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-111">If so, this is a terminating error.</span></span>

- <span data-ttu-id="e793d-112">특정 입력 개체 또는 입력 개체의 하위 집합과 관련 된 오류 조건 입니까?</span><span class="sxs-lookup"><span data-stu-id="e793d-112">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="e793d-113">그럴 경우 종료 되지 않는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-113">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="e793d-114">이 cmdlet은 다른 입력 개체에서 처리가 성공할 수 있는 여러 입력 개체를 허용 하나요?</span><span class="sxs-lookup"><span data-stu-id="e793d-114">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="e793d-115">그럴 경우 종료 되지 않는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-115">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="e793d-116">여러 입력 개체를 사용할 수 있는 cmdlet은 특정 상황이 단일 입력 개체에만 적용 되는 경우에도 종료 및 종료 되지 않는 오류를 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-116">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="e793d-117">Cmdlet은 원하는 수의 입력 개체를 수신 하 고 종료 예외를 throw 하기 전에 원하는 수의 성공 또는 오류 개체를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-117">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="e793d-118">수신 된 입력 개체의 수와 전송 된 성공 및 오류 개체의 수에는 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-118">There's no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="e793d-119">0-1 입력 개체만 허용 하 고 0-1 출력 개체만 생성할 수 있는 cmdlet은 오류를 종료 오류로 처리 하 고 종료 예외를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-119">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="e793d-120">종료 되지 않는 오류 보고</span><span class="sxs-lookup"><span data-stu-id="e793d-120">Reporting nonterminating errors</span></span>

<span data-ttu-id="e793d-121">종료 되지 않는 오류에 대 한 보고는 항상 cmdlet의 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드 또는 system.object 구현 내에서 수행 [해야 합니다 (](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 예를 들어,, 또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ... s a s.).</span><span class="sxs-lookup"><span data-stu-id="e793d-121">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="e793d-122">이러한 오류 유형은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 오류 스트림으로 오류 레코드를 전송 하 여 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-122">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="e793d-123">종료 오류 보고</span><span class="sxs-lookup"><span data-stu-id="e793d-123">Reporting terminating errors</span></span>

<span data-ttu-id="e793d-124">종료 오류는 예외를 throw 하거나 [ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 하 여 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-124">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="e793d-125">또한 cmdlet은 **OutOfMemory** 와 같은 예외를 catch 하 고 다시 throw 할 수 있지만, PowerShell 런타임이 이러한 예외를 catch 하는 것 처럼 예외를 다시 throw 하는 것은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-125">Be aware that cmdlets can also catch and rethrow exceptions such as **OutOfMemory**, however, they aren't required to rethrow exceptions as the PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="e793d-126">상황과 관련 된 문제에 대 한 사용자 고유의 예외를 정의 하거나 해당 오류 레코드를 사용 하 여 기존 예외에 추가 정보를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-126">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="e793d-127">오류 레코드</span><span class="sxs-lookup"><span data-stu-id="e793d-127">Error records</span></span>

<span data-ttu-id="e793d-128">PowerShell에서는 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 사용 하 여 종료 되지 않는 오류 조건을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-128">PowerShell describes a nonterminating error condition with [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="e793d-129">각 개체는 오류 범주 정보, 선택적 대상 개체 및 오류 조건에 대 한 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-129">Each object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="e793d-130">오류 식별자</span><span class="sxs-lookup"><span data-stu-id="e793d-130">Error identifiers</span></span>

<span data-ttu-id="e793d-131">오류 식별자는 cmdlet 내에서 오류 조건을 식별 하는 간단한 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-131">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span>
<span data-ttu-id="e793d-132">PowerShell은이 식별자와 cmdlet 식별자를 결합 하 여 나중에 오류 스트림을 필터링 하거나 오류를 기록 하거나, 특정 오류에 응답할 때 또는 다른 사용자별 작업을 수행할 때 사용할 수 있는 정규화 된 오류 식별자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-132">PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="e793d-133">오류 식별자를 지정할 때는 다음 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-133">The following guidelines should be followed when specifying error identifiers:</span></span>

- <span data-ttu-id="e793d-134">다른 코드 경로에 서로 다른 매우 구체적인 오류 식별자를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-134">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="e793d-135">[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 를 호출 하는 각 코드 경로에는 고유한 오류 식별자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-135">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="e793d-136">오류 식별자는 종료 및 종료 되지 않는 오류 모두에 대 한 CLR (공용 언어 런타임) 예외 유형에 대해 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-136">Error identifiers should be unique to Common Language Runtime (CLR) exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="e793d-137">Cmdlet 또는 PowerShell 공급자의 버전 간에 오류 식별자의 의미 체계를 변경 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="e793d-137">Don't change the semantics of an error identifier between versions of your cmdlet or PowerShell provider.</span></span> <span data-ttu-id="e793d-138">오류 식별자의 의미 체계가 설정 된 후에는 cmdlet의 수명 주기 내내 일정 하 게 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-138">After the semantics of an error identifier is established, it should remain constant throughout the lifecycle of your cmdlet.</span></span>

- <span data-ttu-id="e793d-139">종료 오류의 경우 특정 CLR 예외 유형에 대해 고유한 오류 식별자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-139">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="e793d-140">예외 형식이 변경 되 면 새 오류 식별자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-140">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="e793d-141">종료 되지 않는 오류의 경우 특정 입력 개체에 대 한 특정 오류 식별자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-141">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="e793d-142">보고 되는 오류에 해당 하는 tersely 식별자에 대 한 텍스트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-142">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="e793d-143">공백 또는 문장 부호를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-143">Don't use white space or punctuation.</span></span>

- <span data-ttu-id="e793d-144">재현 하지 않는 오류 식별자는 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-144">Don't generate error identifiers that aren't reproducible.</span></span> <span data-ttu-id="e793d-145">예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-145">For example, don't generate identifiers that include a process identifier.</span></span> <span data-ttu-id="e793d-146">오류 식별자는 동일한 문제가 발생 하는 다른 사용자에 게 표시 되는 식별자에 해당 하는 경우에만 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-146">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="e793d-147">오류 범주</span><span class="sxs-lookup"><span data-stu-id="e793d-147">Error categories</span></span>

<span data-ttu-id="e793d-148">오류 범주는 사용자에 대 한 오류를 그룹화 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-148">Error categories are used to group errors for the user.</span></span> <span data-ttu-id="e793d-149">PowerShell은 이러한 범주 및 cmdlet을 정의 하 고 PowerShell 공급자는 오류 레코드를 생성할 때 이러한 범주와 cmdlet 중 하나를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-149">PowerShell defines these categories and cmdlets and PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="e793d-150">사용할 수 있는 오류 범주에 대 한 설명은 [ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e793d-150">For a description of the error categories that are available, see the [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="e793d-151">일반적으로 가능한 경우 **noerror**, **UndefinedError** 및 **genericerror** 를 사용 하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-151">In general, you should avoid using **NoError**, **UndefinedError**, and **GenericError** whenever possible.</span></span>

<span data-ttu-id="e793d-152">사용자는 `$ErrorView` **categoryview** 로 설정 된 범주에 따라 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e793d-152">Users can view errors based on category when they set `$ErrorView` to **CategoryView**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e793d-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e793d-153">See also</span></span>

[<span data-ttu-id="e793d-154">Cmdlet 개요</span><span class="sxs-lookup"><span data-stu-id="e793d-154">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="e793d-155">Cmdlet 출력 형식</span><span class="sxs-lookup"><span data-stu-id="e793d-155">Types of Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="e793d-156">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="e793d-156">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)
