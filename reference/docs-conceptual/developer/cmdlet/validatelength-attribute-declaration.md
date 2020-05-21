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
ms.openlocfilehash: a1a494534169b2da470286020dfacfa8e9084839
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692318"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="8c590-102">ValidateLength 특성 선언</span><span class="sxs-lookup"><span data-stu-id="8c590-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="8c590-103">ValidateLength 특성은 cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="8c590-104">이 특성은 Windows PowerShell 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c590-105">구문</span><span class="sxs-lookup"><span data-stu-id="8c590-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="8c590-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c590-106">Parameters</span></span>

<span data-ttu-id="8c590-107">`MinLength`([System.web](/dotnet/api/System.Int32))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="8c590-108">허용 되는 최소 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="8c590-109">`MaxLength`([System.web](/dotnet/api/System.Int32))이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="8c590-110">허용 되는 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c590-111">설명</span><span class="sxs-lookup"><span data-stu-id="8c590-111">Remarks</span></span>

- <span data-ttu-id="8c590-112">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [입력 유효성 검사 규칙을 선언 하는 방법](./how-to-validate-parameter-input.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c590-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="8c590-113">이 특성을 사용 하지 않으면 해당 매개 변수 인수의 길이는 모두 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="8c590-114">Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="8c590-115">`MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`</span><span class="sxs-lookup"><span data-stu-id="8c590-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="8c590-116">`MaxLength`특성 매개 변수가 0으로 설정 된 경우</span><span class="sxs-lookup"><span data-stu-id="8c590-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="8c590-117">인수가 문자열이 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="8c590-117">When the argument is not a string.</span></span>

- <span data-ttu-id="8c590-118">ValidateLength 특성은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c590-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c590-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c590-119">See Also</span></span>

[<span data-ttu-id="8c590-120">Validatelengthattribute.</span><span class="sxs-lookup"><span data-stu-id="8c590-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="8c590-121">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="8c590-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
