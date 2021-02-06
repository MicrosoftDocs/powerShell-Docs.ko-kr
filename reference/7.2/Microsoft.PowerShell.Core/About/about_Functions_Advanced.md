---
description: 에서는 스크립트를 사용 하 여 cmdlet을 만드는 방법 인 고급 함수를 소개 합니다.
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599571"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="ea70e-103">함수 고급 정보</span><span class="sxs-lookup"><span data-stu-id="ea70e-103">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="ea70e-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ea70e-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ea70e-105">에서는 스크립트를 사용 하 여 cmdlet을 만드는 방법 인 고급 함수를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-105">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="ea70e-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ea70e-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ea70e-107">Cmdlet은 PowerShell의 파이프라인 의미 체계에 참여 하는 단일 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-107">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="ea70e-108">여기에는 이진 cmdlet, 고급 스크립트 함수, CDXML 및 워크플로가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-108">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="ea70e-109">고급 기능을 사용 하면 PowerShell 함수로 작성 된 cmdlet을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-109">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="ea70e-110">고급 함수를 사용 하면 이진 cmdlet을 작성 하 고 컴파일하지 않고도 cmdlet을 보다 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-110">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="ea70e-111">이진 cmdlet은 c #과 같은 .NET 언어로 작성 된 .NET 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-111">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="ea70e-112">고급 함수 `CmdletBinding` 는 특성을 사용 하 여 cmdlet 처럼 동작 하는 함수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-112">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="ea70e-113">`CmdletBinding`특성은 컴파일된 cmdlet 클래스에서 클래스를 cmdlet으로 식별 하는 데 사용 되는 cmdlet 특성과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-113">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="ea70e-114">이 특성에 대 한 자세한 내용은 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea70e-114">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="ea70e-115">다음 예제에서는 이름을 받아들인 다음 제공 된 이름을 사용 하 여 인사말을 출력 하는 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-115">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="ea70e-116">또한이 함수는 컴파일된 cmdlet의 동사-명사 쌍과 같은 동사 (보내기) 및 명사 (인사말) 쌍을 포함 하는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-116">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="ea70e-117">그러나 함수에는 동사 명사 이름을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-117">However, functions are not required to have a verb-noun name.</span></span>

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

<span data-ttu-id="ea70e-118">함수의 매개 변수는 매개 변수 특성을 사용 하 여 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-118">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="ea70e-119">이 특성은 단독으로 사용 하거나 별칭 특성 또는 다른 여러 매개 변수 유효성 검사 특성과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-119">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="ea70e-120">매개 변수를 선언 하는 방법에 대 한 자세한 내용은 (런타임에 추가 되는 동적 매개 변수 포함) [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea70e-120">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="ea70e-121">이전 함수의 실제 작업은 cmdlet에 전달 되는 데이터를 처리 하기 위해 컴파일된 cmdlet에서 사용 하는 ProcessingRecord 메서드와 동일한 프로세스 블록에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-121">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="ea70e-122">이 블록은 Begin 및 End 블록과 함께 [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) 항목에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-122">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="ea70e-123">고급 함수는 다음과 같은 방법으로 컴파일된 cmdlet과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-123">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="ea70e-124">문자열 배열이 부울 매개 변수에 바인딩되면 고급 함수 매개 변수 바인딩이 예외를 throw 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-124">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="ea70e-125">ValidateSet 특성 및 ValidatePattern 특성은 명명 된 매개 변수를 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-125">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="ea70e-126">고급 함수는 트랜잭션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea70e-126">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea70e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea70e-127">SEE ALSO</span></span>

[<span data-ttu-id="ea70e-128">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ea70e-128">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="ea70e-129">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="ea70e-129">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="ea70e-130">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="ea70e-130">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="ea70e-131">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="ea70e-131">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="ea70e-132">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="ea70e-132">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
