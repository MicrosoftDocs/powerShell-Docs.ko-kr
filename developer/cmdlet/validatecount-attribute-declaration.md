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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067181"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="02fc2-102">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="02fc2-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="02fc2-103">ValidateCount 특성 인수는 cmdlet 매개 변수에 대해 허용 되는 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="02fc2-104">구문</span><span class="sxs-lookup"><span data-stu-id="02fc2-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="02fc2-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="02fc2-105">Parameters</span></span>

<span data-ttu-id="02fc2-106">`MinLength` ([System.Int32][]) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="02fc2-107">최소 인수 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="02fc2-108">`MaxLength`([System.Int32][]) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="02fc2-109">인수의 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="02fc2-110">설명</span><span class="sxs-lookup"><span data-stu-id="02fc2-110">Remarks</span></span>

- <span data-ttu-id="02fc2-111">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [인수 개수를 확인 하는 방법을][]합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="02fc2-112">이 특성은 호출 되지 경우 해당 cmdlet 매개 변수 인수 몇 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="02fc2-113">Windows PowerShell 런타임에 다음과 같은 경우 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="02fc2-114">합니다 `MinLength` 하 고 `MaxLength` 형식이 아닌 특성 매개 변수 [System.Int32][]합니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="02fc2-115">값을 `MaxLength` 특성 매개 변수 값 보다 작습니다는 `MinLength` 특성 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="02fc2-116">ValidateCount 특성은 정의한 합니다 [System.Management.Automation.ValidateCountAttribute][] 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="02fc2-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="02fc2-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02fc2-117">See Also</span></span>

<span data-ttu-id="02fc2-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="02fc2-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="02fc2-119">[인수 개수를 확인 하는 방법을][]</span><span class="sxs-lookup"><span data-stu-id="02fc2-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="02fc2-120">[Writing a Windows PowerShell Cmdlet][](Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="02fc2-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[인수 개수를 확인 하는 방법을]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md(Windows PowerShell Cmdlet 작성)

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
