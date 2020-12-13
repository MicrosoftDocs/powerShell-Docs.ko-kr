---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateLength 특성 선언
description: ValidateLength 특성 선언
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646192"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="9b7b7-103">ValidateLength 특성 선언</span><span class="sxs-lookup"><span data-stu-id="9b7b7-103">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="9b7b7-104">ValidateLength 특성은 cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-104">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="9b7b7-105">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b7b7-106">구문</span><span class="sxs-lookup"><span data-stu-id="9b7b7-106">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="9b7b7-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b7b7-107">Parameters</span></span>

<span data-ttu-id="9b7b7-108">`MinLength` ([System.web](/dotnet/api/System.Int32))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-108">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="9b7b7-109">허용 되는 최소 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-109">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="9b7b7-110">`MaxLength` ([System.web](/dotnet/api/System.Int32))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-110">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="9b7b7-111">허용 되는 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-111">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b7b7-112">설명</span><span class="sxs-lookup"><span data-stu-id="9b7b7-112">Remarks</span></span>

- <span data-ttu-id="9b7b7-113">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [입력 유효성 검사 규칙을 선언 하는 방법](./how-to-validate-parameter-input.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="9b7b7-114">이 특성을 사용 하지 않으면 해당 매개 변수 인수의 길이는 모두 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="9b7b7-115">Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="9b7b7-116">`MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`</span><span class="sxs-lookup"><span data-stu-id="9b7b7-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="9b7b7-117">`MaxLength`특성 매개 변수가 0으로 설정 된 경우</span><span class="sxs-lookup"><span data-stu-id="9b7b7-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="9b7b7-118">인수가 문자열이 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="9b7b7-118">When the argument is not a string.</span></span>

- <span data-ttu-id="9b7b7-119">ValidateLength 특성은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b7b7-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b7b7-120">See Also</span></span>

[<span data-ttu-id="9b7b7-121">Validatelengthattribute.</span><span class="sxs-lookup"><span data-stu-id="9b7b7-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

<span data-ttu-id="9b7b7-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9b7b7-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
