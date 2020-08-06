---
title: ValidateCount 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.openlocfilehash: c013a354ee339bd14508fe30549673bc79d5c616
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786325"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="a2d75-102">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="a2d75-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="a2d75-103">ValidateCount 특성은 cmdlet 매개 변수에 허용 되는 인수의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2d75-104">구문</span><span class="sxs-lookup"><span data-stu-id="a2d75-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="a2d75-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a2d75-105">Parameters</span></span>

<span data-ttu-id="a2d75-106">`MinLength`([System.web][])이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="a2d75-107">인수의 최소 개수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="a2d75-108">`MaxLength`([System.web][])이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="a2d75-109">최대 인수 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2d75-110">설명</span><span class="sxs-lookup"><span data-stu-id="a2d75-110">Remarks</span></span>

- <span data-ttu-id="a2d75-111">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [인수 수의 유효성을 검사][]하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2d75-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="a2d75-112">이 특성이 호출 되지 않으면 해당 cmdlet 매개 변수에 원하는 수의 인수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="a2d75-113">Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="a2d75-114">`MinLength`및 `MaxLength` 특성 매개 변수는 [system.object][]형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="a2d75-115">`MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`</span><span class="sxs-lookup"><span data-stu-id="a2d75-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="a2d75-116">ValidateCount 특성은 [ValidateCountAttribute][] 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d75-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2d75-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2d75-117">See Also</span></span>

<span data-ttu-id="a2d75-118">[ValidateCountAttribute.][]</span><span class="sxs-lookup"><span data-stu-id="a2d75-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="a2d75-119">[인수 개수를 확인하는 방법][]</span><span class="sxs-lookup"><span data-stu-id="a2d75-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="a2d75-120">[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)][]</span><span class="sxs-lookup"><span data-stu-id="a2d75-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[인수 개수를 확인하는 방법]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute.]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
