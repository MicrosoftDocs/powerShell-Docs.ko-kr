---
title: Cmdlet 코드의 예 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068201"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="a58cf-102">Cmdlet 코드 예제</span><span class="sxs-lookup"><span data-stu-id="a58cf-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="a58cf-103">이 섹션에서는 사용자 고유의 cmdlet을 작성 하려면 사용할 수 있는 cmdlet 코드의 예제를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a58cf-104">Cmdlet을 작성 하기 위한 단계별 지침을 참조 하세요 [작성 하는 Cmdlet에 대 한 자습서](./tutorials-for-writing-cmdlets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a58cf-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="a58cf-105">In This Section</span></span>

<span data-ttu-id="a58cf-106">[간단한 Cmdlet을 작성 하는 방법을](./how-to-write-a-simple-cmdlet.md) 이 예제에서는 cmdlet 코드의 기본 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="a58cf-107">[Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md) 이 예제에서는 다양 한 유형의 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="a58cf-108">[선언 매개 변수를 설정 하는 방법을](./how-to-declare-parameter-sets.md) 이 예제 cmdlet에서 수행 하는 동작을 변경할 수 있는 매개 변수 집합을 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="a58cf-109">[매개 변수 입력 유효성 검사 방법](./how-to-validate-parameter-input.md) 이러한 예제 매개 변수 입력의 유효성을 검사 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="a58cf-110">[동적 매개 변수를 선언 하는 방법을](./how-to-declare-dynamic-parameters.md) 이 예제에서는 런타임에 추가 되는 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="a58cf-111">[Cmdlet 내에서 스크립트를 호출 하는 방법을](./how-to-invoke-scripts-within-a-cmdlet.md) 이 예제 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="a58cf-112">[입력 처리 메서드를 재정의 하는 방법을](./how-to-override-input-processing-methods.md) 이러한 예제에서는 BeginProcessing 고 ProcessRecord, EndProcessing 메서드를 재정의 하는 데 기본 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="a58cf-113">[지원 ShouldProcess 호출 하는 방법](./how-to-request-confirmations.md) 보여 주는이 예제는 방법을 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) cmdlet 내에서 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="a58cf-114">[트랜잭션 지원 방법](./how-to-support-transactions.md) 이 예제에서는 cmdlet에서 트랜잭션을 지원 하도록 지정 하는 방법 및 cmdlet은 트랜잭션 내에서 사용 되는 경우 수행 되는 작업을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="a58cf-115">[지원 작업 방법](./how-to-support-jobs.md) 이 예제에서는 cmdlet을 작성 하는 경우 작업을 지 원하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="a58cf-116">[Cmdlet에서 내는 Cmdlet을 호출 하는 방법을](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) 호출된 cmdlet의 기능을 개발 하는 cmdlet에 추가할 수 있는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 주는이 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="a58cf-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="a58cf-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a58cf-117">See Also</span></span>

<span data-ttu-id="a58cf-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a58cf-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
