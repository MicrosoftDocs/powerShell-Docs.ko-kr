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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364502"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="d339a-102">Cmdlet 코드 예제</span><span class="sxs-lookup"><span data-stu-id="d339a-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="d339a-103">이 섹션에는 사용자 고유의 cmdlet 작성을 시작 하는 데 사용할 수 있는 cmdlet 코드 예제가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d339a-104">Cmdlet을 작성 하는 방법에 대 한 단계별 지침은 [Cmdlet 작성을 위한 자습서](./tutorials-for-writing-cmdlets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d339a-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d339a-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="d339a-105">In This Section</span></span>

<span data-ttu-id="d339a-106">[간단한 Cmdlet을 작성 하는 방법](./how-to-write-a-simple-cmdlet.md) 이 예제에서는 cmdlet 코드의 기본 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="d339a-107">[Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md) 이 예제에서는 다양 한 형식의 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="d339a-108">[매개 변수 집합을 선언 하는 방법](./how-to-declare-parameter-sets.md) 이 예제에서는 cmdlet이 수행 하는 동작을 변경할 수 있는 매개 변수 집합을 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="d339a-109">[매개 변수 입력의 유효성을 검사 하는 방법](./how-to-validate-parameter-input.md) 다음 예제에서는 매개 변수 입력의 유효성을 검사 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="d339a-110">[동적 매개 변수를 선언 하는 방법](./how-to-declare-dynamic-parameters.md) 이 예제에서는 런타임에 추가 되는 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="d339a-111">[Cmdlet 내에서 스크립트를 호출 하는 방법](./how-to-invoke-scripts-within-a-cmdlet.md) 이 예제에서는 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="d339a-112">[입력 처리 메서드를 재정의 하는 방법](./how-to-override-input-processing-methods.md) 다음 예제에서는 BeginProcessing, ProcessRecord 및 EndProcessing 메서드를 재정의 하는 데 사용 되는 기본 구조를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="d339a-113">[ShouldProcess 호출을 지 원하는 방법](./how-to-request-confirmations.md) 이 예제에서는 cmdlet 내에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) [를 호출](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 하는 방법에 대해 설명 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="d339a-114">[트랜잭션을 지 원하는 방법](./how-to-support-transactions.md) 이 예에서는 cmdlet이 트랜잭션을 지원 함을 나타내는 방법과 트랜잭션 내에서 cmdlet을 사용할 때 수행 되는 동작을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="d339a-115">[작업 지원 방법](./how-to-support-jobs.md) 이 예제에서는 cmdlet을 작성할 때 작업을 지 원하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="d339a-116">[Cmdlet에서 cmdlet을 호출 하는 방법](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) 이 예에서는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다 .이 cmdlet을 사용 하면 호출 되는 cmdlet의 기능을 개발 중인 cmdlet에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d339a-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="d339a-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d339a-117">See Also</span></span>

<span data-ttu-id="d339a-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d339a-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
