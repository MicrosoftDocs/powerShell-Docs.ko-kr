---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateSet 특성 선언
description: ValidateSet 특성 선언
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660467"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="275b0-103">ValidateSet 특성 선언</span><span class="sxs-lookup"><span data-stu-id="275b0-103">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="275b0-104">ValidateSetAttribute 특성은 cmdlet 매개 변수 인수에 사용할 수 있는 값의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-104">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="275b0-105">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="275b0-106">이 특성이 지정 된 경우 Windows PowerShell 런타임에서는 cmdlet 매개 변수에 대해 제공 된 인수가 제공 된 요소 집합의 요소와 일치 하는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-106">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="275b0-107">Cmdlet은 매개 변수 인수가 집합의 요소와 일치 하는 경우에만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-107">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="275b0-108">일치 하는 항목이 없으면 Windows PowerShell 런타임에서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-108">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="275b0-109">구문</span><span class="sxs-lookup"><span data-stu-id="275b0-109">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="275b0-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="275b0-110">Parameters</span></span>

<span data-ttu-id="275b0-111">`ValidValues` ([System.string](/dotnet/api/System.String))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-111">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="275b0-112">유효한 매개 변수 요소 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-112">Specifies the valid parameter element values.</span></span> <span data-ttu-id="275b0-113">다음 샘플에서는 하나 또는 여러 요소를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-113">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="275b0-114">`IgnoreCase` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-114">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="275b0-115">기본값은 `true` 대/소문자가 무시 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-115">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="275b0-116">값을 `false` 사용 하면 cmdlet에서 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-116">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="275b0-117">설명</span><span class="sxs-lookup"><span data-stu-id="275b0-117">Remarks</span></span>

- <span data-ttu-id="275b0-118">이 특성은 매개 변수 당 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-118">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="275b0-119">매개 변수 값이 배열인 경우 배열의 모든 요소는 특성 집합의 요소와 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-119">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="275b0-120">ValidateSetAttribute 특성은 [ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="275b0-120">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="275b0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="275b0-121">See Also</span></span>

[<span data-ttu-id="275b0-122">Validatesetattribute.</span><span class="sxs-lookup"><span data-stu-id="275b0-122">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

<span data-ttu-id="275b0-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="275b0-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
