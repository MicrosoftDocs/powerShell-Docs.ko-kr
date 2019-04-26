---
title: ValidateRange 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067113"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="b8907-102">ValidateRange 특성 선언</span><span class="sxs-lookup"><span data-stu-id="b8907-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="b8907-103">ValidateRange 특성 cmdlet 매개 변수 인수에 대 한 최소 및 최대 값 (범위)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="b8907-104">Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8907-105">구문</span><span class="sxs-lookup"><span data-stu-id="b8907-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="b8907-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b8907-106">Parameters</span></span>

<span data-ttu-id="b8907-107">`MinRange` ([System.Object](/dotnet/api/system.object)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="b8907-108">허용 되는 최소값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="b8907-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="b8907-110">허용 되는 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8907-111">설명</span><span class="sxs-lookup"><span data-stu-id="b8907-111">Remarks</span></span>

- <span data-ttu-id="b8907-112">Windows PowerShell 런타임 생성 오류를 throw 때의 값을 `MinRange` 매개 변수 값 보다 큽니다.는 `MaxRange` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="b8907-113">Windows PowerShell 런타임에 다음과 같은 유효성 검사 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="b8907-114">인수의 값이 보다 작은 `MinRange` 제한 보다 크거나는 `MaxRange` 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="b8907-115">인수가 없는 경우와 동일한 형식의 합니다 `MinRange` 하며 `MaxRange` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="b8907-116">ValidateRange 특성은 정의한 합니다 [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b8907-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8907-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8907-117">See Also</span></span>

[<span data-ttu-id="b8907-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="b8907-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

<span data-ttu-id="b8907-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b8907-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
