---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateRange 특성 선언
description: ValidateRange 특성 선언
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660599"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="aa2e0-103">ValidateRange 특성 선언</span><span class="sxs-lookup"><span data-stu-id="aa2e0-103">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="aa2e0-104">ValidateRange 특성은 cmdlet 매개 변수 인수에 대 한 최소값 및 최대값 (범위)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-104">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="aa2e0-105">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa2e0-106">구문</span><span class="sxs-lookup"><span data-stu-id="aa2e0-106">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="aa2e0-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="aa2e0-107">Parameters</span></span>

<span data-ttu-id="aa2e0-108">`MinRange` ([System.object](/dotnet/api/system.object))가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-108">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="aa2e0-109">허용 되는 최소값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-109">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="aa2e0-110">`MaxRange` ([System.object](/dotnet/api/system.object))가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-110">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="aa2e0-111">허용 되는 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-111">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa2e0-112">설명</span><span class="sxs-lookup"><span data-stu-id="aa2e0-112">Remarks</span></span>

- <span data-ttu-id="aa2e0-113">Windows PowerShell 런타임에서는 `MinRange` 매개 변수 값이 매개 변수 값 보다 클 때 생성 오류를 throw 합니다 `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="aa2e0-113">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="aa2e0-114">Windows PowerShell 런타임은 다음과 같은 경우 유효성 검사 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-114">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="aa2e0-115">인수의 값이 제한 보다 작거나 한 `MinRange` 도 보다 큰 경우 `MaxRange`</span><span class="sxs-lookup"><span data-stu-id="aa2e0-115">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="aa2e0-116">인수가 `MinRange` 및 매개 변수와 동일한 형식이 아닌 경우 `MaxRange`</span><span class="sxs-lookup"><span data-stu-id="aa2e0-116">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="aa2e0-117">ValidateRange 특성은 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-117">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa2e0-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa2e0-118">See Also</span></span>

[<span data-ttu-id="aa2e0-119">Validaterangeattribute.</span><span class="sxs-lookup"><span data-stu-id="aa2e0-119">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

<span data-ttu-id="aa2e0-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="aa2e0-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
