---
title: ValidateCount 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794447"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="b2971-102">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="b2971-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="b2971-103">ValidateCount 특성 인수는 cmdlet 매개 변수에 대해 허용 되는 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2971-104">구문</span><span class="sxs-lookup"><span data-stu-id="b2971-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="b2971-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b2971-105">Parameters</span></span>

<span data-ttu-id="b2971-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="b2971-107">최소 인수 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="b2971-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="b2971-109">인수의 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2971-110">설명</span><span class="sxs-lookup"><span data-stu-id="b2971-110">Remarks</span></span>

- <span data-ttu-id="b2971-111">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [입력 유효성 검사 규칙 선언 하는 방법을](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="b2971-112">이 특성은 호출 되지 경우 해당 cmdlet 매개 변수 인수 몇 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="b2971-113">Windows PowerShell 런타임에 다음과 같은 경우 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="b2971-114">합니다 `MinLength` 하 고 `MaxLength` 형식이 아닌 특성 매개 변수 [System.Int32](/dotnet/api/System.Int32)합니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="b2971-115">값을 `MaxLength` 특성 매개 변수 값 보다 작습니다는 `MinLength` 특성 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="b2971-116">ValidateCount 특성은 정의한 합니다 [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b2971-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2971-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2971-117">See Also</span></span>

[<span data-ttu-id="b2971-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="b2971-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="b2971-119">입력된 유효성 검사 규칙을 선언 하는 방법</span><span class="sxs-lookup"><span data-stu-id="b2971-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

<span data-ttu-id="b2971-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b2971-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
