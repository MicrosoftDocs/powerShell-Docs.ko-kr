---
title: ValidateSet 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787770"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="110e4-102">ValidateSet 특성 선언</span><span class="sxs-lookup"><span data-stu-id="110e4-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="110e4-103">ValidateSetAttribute 특성은 cmdlet 매개 변수 인수에 사용할 수 있는 값의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="110e4-104">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="110e4-105">이 특성이 지정 된 경우 Windows PowerShell 런타임에서는 cmdlet 매개 변수에 대해 제공 된 인수가 제공 된 요소 집합의 요소와 일치 하는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="110e4-106">Cmdlet은 매개 변수 인수가 집합의 요소와 일치 하는 경우에만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="110e4-107">일치 하는 항목이 없으면 Windows PowerShell 런타임에서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="110e4-108">구문</span><span class="sxs-lookup"><span data-stu-id="110e4-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="110e4-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="110e4-109">Parameters</span></span>

<span data-ttu-id="110e4-110">`ValidValues`([System.string](/dotnet/api/System.String))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="110e4-111">유효한 매개 변수 요소 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="110e4-112">다음 샘플에서는 하나 또는 여러 요소를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="110e4-113">`IgnoreCase`([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="110e4-114">기본값은 `true` 대/소문자가 무시 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="110e4-115">값을 `false` 사용 하면 cmdlet에서 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="110e4-116">설명</span><span class="sxs-lookup"><span data-stu-id="110e4-116">Remarks</span></span>

- <span data-ttu-id="110e4-117">이 특성은 매개 변수 당 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="110e4-118">매개 변수 값이 배열인 경우 배열의 모든 요소는 특성 집합의 요소와 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="110e4-119">ValidateSetAttribute 특성은 [ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="110e4-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="110e4-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="110e4-120">See Also</span></span>

[<span data-ttu-id="110e4-121">Validatesetattribute.</span><span class="sxs-lookup"><span data-stu-id="110e4-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="110e4-122">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="110e4-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
