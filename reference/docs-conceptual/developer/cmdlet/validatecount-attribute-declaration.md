---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateCount 특성 선언
description: ValidateCount 특성 선언
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646276"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="b0b80-103">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="b0b80-103">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="b0b80-104">ValidateCount 특성은 cmdlet 매개 변수에 허용 되는 인수의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-104">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0b80-105">구문</span><span class="sxs-lookup"><span data-stu-id="b0b80-105">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="b0b80-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b0b80-106">Parameters</span></span>

<span data-ttu-id="b0b80-107">`MinLength` ([System.web][])이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-107">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="b0b80-108">인수의 최소 개수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-108">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="b0b80-109">`MaxLength`([System.web][])이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-109">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="b0b80-110">최대 인수 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-110">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0b80-111">설명</span><span class="sxs-lookup"><span data-stu-id="b0b80-111">Remarks</span></span>

- <span data-ttu-id="b0b80-112">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [인수 수의 유효성을 검사][]하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b0b80-112">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="b0b80-113">이 특성이 호출 되지 않으면 해당 cmdlet 매개 변수에 원하는 수의 인수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-113">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="b0b80-114">Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="b0b80-115">`MinLength`및 `MaxLength` 특성 매개 변수는 [system.object][]형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-115">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="b0b80-116">`MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`</span><span class="sxs-lookup"><span data-stu-id="b0b80-116">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="b0b80-117">ValidateCount 특성은 [ValidateCountAttribute][] 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0b80-117">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0b80-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0b80-118">See Also</span></span>

<span data-ttu-id="b0b80-119">[ValidateCountAttribute.][]</span><span class="sxs-lookup"><span data-stu-id="b0b80-119">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="b0b80-120">[인수 개수를 확인하는 방법][]</span><span class="sxs-lookup"><span data-stu-id="b0b80-120">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="b0b80-121">[Writing a Windows PowerShell Cmdlet][](Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b0b80-121">[Writing a Windows PowerShell Cmdlet][]</span></span>

[인수 개수를 확인하는 방법]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md(Windows PowerShell Cmdlet 작성)

[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute.]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
