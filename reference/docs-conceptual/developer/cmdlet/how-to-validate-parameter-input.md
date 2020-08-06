---
title: 매개 변수 입력의 유효성을 검사 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f3e43ae4cd421e2beea9ef8419c87e818ed65b6b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781939"
---
# <a name="how-to-validate-parameter-input"></a><span data-ttu-id="7dae3-102">매개 변수 입력 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="7dae3-102">How to Validate Parameter Input</span></span>

<span data-ttu-id="7dae3-103">이 섹션에서는 다양 한 특성을 사용 하 여 유효성 검사 규칙을 구현 하 여 매개 변수 입력의 유효성을 검사 하는 방법을 보여 주는 예제</span><span class="sxs-lookup"><span data-stu-id="7dae3-103">This section contains examples that show how to validate parameter input by using various attributes to implement validation rules.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7dae3-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7dae3-104">In This Section</span></span>

<span data-ttu-id="7dae3-105">[인수 집합의 유효성을 검사 하는 방법](./how-to-validate-an-argument-set.md) ArgumentSet 특성을 사용 하 여 인수 집합의 유효성을 검사 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dae3-105">[How to Validate an Argument Set](./how-to-validate-an-argument-set.md) Describes how to validate an argument set by using the ArgumentSet attribute.</span></span>

<span data-ttu-id="7dae3-106">[인수 범위의 유효성을 검사 하는 방법](./how-to-validate-an-argument-range.md) ArgumentRange 특성을 사용 하 여 인수 범위의 유효성을 검사 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dae3-106">[How to Validate an Argument Range](./how-to-validate-an-argument-range.md) Describes how to validate an argument range by using the ArgumentRange attribute.</span></span>

<span data-ttu-id="7dae3-107">[인수 패턴의 유효성을 검사 하는 방법](./how-to-validate-an-argument-pattern.md) ArgumentPattern 특성을 사용 하 여 인수 패턴의 유효성을 검사 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dae3-107">[How to Validate an Argument Pattern](./how-to-validate-an-argument-pattern.md) Describes how to validate an argument pattern by using the ArgumentPattern attribute.</span></span>

<span data-ttu-id="7dae3-108">[인수 길이를 확인 하는 방법](./how-to-validate-the-argument-length.md) ArgumentLength 특성을 사용 하 여 인수의 길이를 확인 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dae3-108">[How to Validate the Argument Length](./how-to-validate-the-argument-length.md) Describes how to validate the length of an argument by using the ArgumentLength attribute.</span></span>

<span data-ttu-id="7dae3-109">[인수 수의 유효성을 검사 하는 방법](./how-to-validate-an-argument-count.md) ArgumentCount 특성을 사용 하 여 인수 수의 유효성을 검사 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dae3-109">[How to Validate an Argument Count](./how-to-validate-an-argument-count.md) Describes how to validate an argument count by using the ArgumentCount attribute.</span></span>

<span data-ttu-id="7dae3-110">매개 변수가 선언 되는 방식은 유효성 검사에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dae3-110">The way a parameter is declared can affect validation.</span></span> <span data-ttu-id="7dae3-111">자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7dae3-111">For more information, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

## <a name="reference"></a><span data-ttu-id="7dae3-112">참조</span><span class="sxs-lookup"><span data-stu-id="7dae3-112">Reference</span></span>

## <a name="see-also"></a><span data-ttu-id="7dae3-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7dae3-113">See Also</span></span>

[<span data-ttu-id="7dae3-114">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="7dae3-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
