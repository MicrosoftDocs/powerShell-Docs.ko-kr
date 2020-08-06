---
title: ValidateRange 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.openlocfilehash: 9aeaa6f03c170389ff61a058b505dbcf74df6958
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787787"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="114a4-102">ValidateRange 특성 선언</span><span class="sxs-lookup"><span data-stu-id="114a4-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="114a4-103">ValidateRange 특성은 cmdlet 매개 변수 인수에 대 한 최소값 및 최대값 (범위)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="114a4-104">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="114a4-105">구문</span><span class="sxs-lookup"><span data-stu-id="114a4-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="114a4-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="114a4-106">Parameters</span></span>

<span data-ttu-id="114a4-107">`MinRange`([System.object](/dotnet/api/system.object))가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="114a4-108">허용 되는 최소값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="114a4-109">`MaxRange`([System.object](/dotnet/api/system.object))가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="114a4-110">허용 되는 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="114a4-111">설명</span><span class="sxs-lookup"><span data-stu-id="114a4-111">Remarks</span></span>

- <span data-ttu-id="114a4-112">Windows PowerShell 런타임에서는 `MinRange` 매개 변수 값이 매개 변수 값 보다 클 때 생성 오류를 throw 합니다 `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="114a4-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="114a4-113">Windows PowerShell 런타임은 다음과 같은 경우 유효성 검사 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="114a4-114">인수의 값이 제한 보다 작거나 한 `MinRange` 도 보다 큰 경우 `MaxRange`</span><span class="sxs-lookup"><span data-stu-id="114a4-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="114a4-115">인수가 `MinRange` 및 매개 변수와 동일한 형식이 아닌 경우 `MaxRange`</span><span class="sxs-lookup"><span data-stu-id="114a4-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="114a4-116">ValidateRange 특성은 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="114a4-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="114a4-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="114a4-117">See Also</span></span>

[<span data-ttu-id="114a4-118">Validaterangeattribute.</span><span class="sxs-lookup"><span data-stu-id="114a4-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="114a4-119">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="114a4-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
