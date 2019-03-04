---
title: ValidateLength 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858869"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="a8e90-102">ValidateLength 특성 선언</span><span class="sxs-lookup"><span data-stu-id="a8e90-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="a8e90-103">ValidateLength 특성 cmdlet 매개 변수 인수에 대 한 문자의 최소 및 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="a8e90-104">Windows PowerShell 함수에서이 특성을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8e90-105">구문</span><span class="sxs-lookup"><span data-stu-id="a8e90-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="a8e90-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a8e90-106">Parameters</span></span>

<span data-ttu-id="a8e90-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="a8e90-108">허용 되는 문자의 최소 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="a8e90-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="a8e90-110">허용 되는 문자의 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8e90-111">설명</span><span class="sxs-lookup"><span data-stu-id="a8e90-111">Remarks</span></span>

- <span data-ttu-id="a8e90-112">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [입력 유효성 검사 규칙 선언 하는 방법을](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="a8e90-113">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [입력 유효성 검사 규칙 선언 하는 방법을](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="a8e90-114">이 특성을 사용 하지 않으면 해당 매개 변수 인수 길이 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="a8e90-115">Windows PowerShell 런타임에 다음과 같은 경우 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="a8e90-116">때의 값을 `MaxLength` 특성 매개 변수 값 보다 작습니다는 `MinLength` 특성 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="a8e90-117">경우는 `MaxLength` 특성 매개 변수는 0으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="a8e90-118">경우 인수 문자열이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-118">When the argument is not a string.</span></span>

- <span data-ttu-id="a8e90-119">ValidateLength 특성은 정의한 합니다 [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e90-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8e90-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8e90-120">See Also</span></span>

[<span data-ttu-id="a8e90-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="a8e90-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

<span data-ttu-id="a8e90-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a8e90-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
