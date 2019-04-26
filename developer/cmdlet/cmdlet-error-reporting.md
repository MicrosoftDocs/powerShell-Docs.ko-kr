---
title: Cmdlet은 오류 보고 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068592"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="80837-102">Cmdlet 오류 보고</span><span class="sxs-lookup"><span data-stu-id="80837-102">Cmdlet Error Reporting</span></span>

<span data-ttu-id="80837-103">Cmdlet 오류는 오류를 종료 하는 여부에 따라 다르게 오류 또는 종료 되지 않는 오류를 보고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-103">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="80837-104">종료 오류는 파이프라인을 즉시 종료 하는 오류 또는 처리를 계속할 필요가 없는 경우 발생 하는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-104">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there is no reason to continue processing.</span></span> <span data-ttu-id="80837-105">종료 되지 않는 오류는 현재 오류 조건을 보고 하는 해당 오류 있지만 cmdlet을 계속 입력된 개체를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-105">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="80837-106">종료 되지 않는 오류를 사용 하 여 사용자가 일반적으로 문제의 알림을 있지만 cmdlet은 다음 입력된 개체를 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80837-106">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="80837-107">종료 및 종료 되지 않는 오류</span><span class="sxs-lookup"><span data-stu-id="80837-107">Terminating and Nonterminating Errors</span></span>

<span data-ttu-id="80837-108">종료 오류 또는 종료 되지 않는 오류를 오류 상태 인지 확인 하려면 다음 지침을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-108">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="80837-109">오류 조건을 사용할 수 없게 cmdlet을 추가로 입력된 개체를 성공적으로 처리?</span><span class="sxs-lookup"><span data-stu-id="80837-109">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="80837-110">그렇다면 종료 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-110">If so, this is a terminating error.</span></span>

- <span data-ttu-id="80837-111">특정 입력된 개체에서 입력된 개체의 하위 집합에 관련 된 오류 조건?</span><span class="sxs-lookup"><span data-stu-id="80837-111">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="80837-112">그렇다면 종료 되지 않는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-112">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="80837-113">Cmdlet은 다른 입력된 개체에 대해 배포할 수 있습니다. 처리는 이러한 여러 입력된 개체를 받아들이지?</span><span class="sxs-lookup"><span data-stu-id="80837-113">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="80837-114">그렇다면 종료 되지 않는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-114">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="80837-115">여러 개의 입력된 개체를 적용할 수 있는 Cmdlet은 특정 상황만 단일 입력된 개체에 적용 하는 경우에 종료 하는 종료 되지 않는 오류 사이의 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-115">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="80837-116">Cmdlet 임의 개수의 입력된 개체를 수신 하 고 종료 예외를 throw 하기 전에 임의 개수의 성공 또는 오류 개체를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-116">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="80837-117">받은 입력된 개체의 수와 전송 성공 및 오류 개체 수 간의 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-117">There is no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="80837-118">0-1만 개체를 입력 하 고만 0-1 생성 적용할 수 있는 Cmdlet에는 개체를 종료 오류를 오류로 처리 하 고 종료 예외를 생성 해야 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-118">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="80837-119">종료 되지 않는 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-119">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="80837-120">종료 되지 않는 오류를 보고 해야 항상 내에서 수행할 cmdlet의 구현의 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드를 [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드 또는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="80837-120">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="80837-121">호출에서 이러한 종류의 오류를 보고 합니다 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 오류 스트림에 오류 레코드를 다시 전송 하는 메서드.</span><span class="sxs-lookup"><span data-stu-id="80837-121">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="80837-122">종료 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-122">Reporting Terminating Errors</span></span>

<span data-ttu-id="80837-123">예외를 throw 하거나 호출 하 여 종료 오류를 보고 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드.</span><span class="sxs-lookup"><span data-stu-id="80837-123">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="80837-124">그러나 Windows PowerShell 런타임도 catch는으로 다시 예외를 throw 할 필요 하지 않습니다도 catch 하 고 다시 OutOfMemory 같은 예외를 throw 할 수 있습니다 cmdlet에 주의 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-124">Be aware that cmdlets can also catch and re-throw exceptions such as OutOfMemory, however, they are not required to re-throw exceptions as the Windows PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="80837-125">또한 해당 오류 레코드를 사용 하 여 기존 예외에 정보를 추가 하거나 상황에 관련 된 문제에 대 한 사용자 고유의 예외를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-125">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="80837-126">오류 레코드</span><span class="sxs-lookup"><span data-stu-id="80837-126">Error Records</span></span>

<span data-ttu-id="80837-127">Windows PowerShell 사용 하 여 종료 되지 않는 오류 조건을 설명 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-127">Windows PowerShell describes a nonterminating error condition through the use of [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="80837-128">각 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체는 오류 범주 정보, 선택적 대상 개체 및 오류 조건에 대 한 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-128">Each [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="80837-129">오류 식별자</span><span class="sxs-lookup"><span data-stu-id="80837-129">Error Identifiers</span></span>

<span data-ttu-id="80837-130">오류 식별자는 간단한 문자열을 cmdlet 내에서 오류 조건을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-130">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span> <span data-ttu-id="80837-131">Windows PowerShell cmdlet은 식별자를 나중에 특정 오류에 응답할 때 오류 스트림 또는 오류를 필터링 하는 경우에 사용할 수 있는 정규화 된 오류 식별자를 만들 수 있는 또는 다른 사용자 고유의 활동을 사용 하 여이 식별자를 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-131">Windows PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="80837-132">오류 식별자를 지정 하는 경우 다음 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-132">The following guidelines should be followed when specifying error identifiers.</span></span>

- <span data-ttu-id="80837-133">서로 다른 코드 경로에 다른 항상 특정 오류 식별자를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-133">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="80837-134">호출 하는 각 코드 경로 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 하거나 [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 고유 오류 식별자 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-134">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="80837-135">오류 식별자 종료 및 종료 되지 않는 오류에 대 한 CLR 예외 형식으로 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-135">Error identifiers should be unique to CLR exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="80837-136">Cmdlet 또는 Windows PowerShell 공급자의 버전 간에 오류 식별자의 의미 체계를 변경 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="80837-136">Do not change the semantics of an error identifier between versions of your cmdlet or Windows PowerShell provider.</span></span> <span data-ttu-id="80837-137">오류 식별자의 의미 체계 설정 되 면 cmdlet의 수명 주기 전체에서 일정 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-137">After the semantics of an error identifier is established, it should remain constant throughout the life cycle of your cmdlet.</span></span>

- <span data-ttu-id="80837-138">종료 오류에 대 한 특정 CLR 예외 형식에 대 한 고유 오류 식별자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-138">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="80837-139">예외 형식을 변경 하는 경우 새 오류 식별자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-139">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="80837-140">종료 되지 않는 오류에 대 한 특정 입력된 개체에 대 한 특정 오류 식별자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-140">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="80837-141">상품 보고 된 오류에 해당 하는 식별자에 대 한 텍스트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-141">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="80837-142">공백 또는 문장 부호를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="80837-142">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="80837-143">재현 가능 하지 않은 오류 식별자를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-143">Do not generate error identifiers that are not reproducible.</span></span> <span data-ttu-id="80837-144">예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80837-144">For example, do not generate identifiers that include a process identifier.</span></span> <span data-ttu-id="80837-145">오류 식별자는 다른 사용자가 동일한 문제가 발생 하는 표시 되는 식별자에 해당 하는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-145">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="80837-146">오류 범주</span><span class="sxs-lookup"><span data-stu-id="80837-146">Error Categories</span></span>

<span data-ttu-id="80837-147">오류 범주는 최종 사용자에 대 한 오류를 그룹화 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80837-147">Error categories are used to group errors for the end-user.</span></span> <span data-ttu-id="80837-148">이러한 범주를 정의 하는 Windows PowerShell 및 cmdlet과 Windows PowerShell 공급자 오류 레코드를 생성 하는 경우 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80837-148">Windows PowerShell defines these categories and cmdlets and Windows PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="80837-149">사용할 수 있는 오류 범주에 대 한 참조를 [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-149">For a description of the error categories that are available, see the [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="80837-150">일반적으로 사용 가능한 GenericError noerror 였습니다, UndefinedError, 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80837-150">In general, you should avoid using NoError, UndefinedError, and GenericError whenever possible.</span></span>

<span data-ttu-id="80837-151">사용자 범주를 기반으로 설정 하는 경우 오류를 볼 수 있습니다 "`$ErrorView`"를 "CategoryView"입니다.</span><span class="sxs-lookup"><span data-stu-id="80837-151">Users can view errors based on category when they set "`$ErrorView`" to "CategoryView".</span></span>

## <a name="see-also"></a><span data-ttu-id="80837-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80837-152">See Also</span></span>

[<span data-ttu-id="80837-153">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80837-153">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="80837-154">Cmdlet 출력</span><span class="sxs-lookup"><span data-stu-id="80837-154">Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="80837-155">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="80837-155">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
