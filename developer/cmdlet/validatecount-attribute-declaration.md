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
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983901"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="2a4a6-102">ValidateCount 특성 선언</span><span class="sxs-lookup"><span data-stu-id="2a4a6-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="2a4a6-103">ValidateCount 특성 인수는 cmdlet 매개 변수에 대해 허용 되는 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a4a6-104">구문</span><span class="sxs-lookup"><span data-stu-id="2a4a6-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="2a4a6-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2a4a6-105">Parameters</span></span>

<span data-ttu-id="2a4a6-106">`MinLength` ([System.Int32][]) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="2a4a6-107">최소 인수 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="2a4a6-108">`MaxLength`([System.Int32][]) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="2a4a6-109">인수의 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a4a6-110">설명</span><span class="sxs-lookup"><span data-stu-id="2a4a6-110">Remarks</span></span>

- <span data-ttu-id="2a4a6-111">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [인수 개수를 확인 하는 방법을][]합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="2a4a6-112">이 특성은 호출 되지 경우 해당 cmdlet 매개 변수 인수 몇 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="2a4a6-113">Windows PowerShell 런타임에 다음과 같은 경우 오류가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="2a4a6-114">합니다 `MinLength` 하 고 `MaxLength` 형식이 아닌 특성 매개 변수 [System.Int32][]합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="2a4a6-115">값을 `MaxLength` 특성 매개 변수 값 보다 작습니다는 `MinLength` 특성 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="2a4a6-116">ValidateCount 특성은 정의한 합니다 [System.Management.Automation.ValidateCountAttribute][] 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="2a4a6-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a4a6-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a4a6-117">See Also</span></span>

<span data-ttu-id="2a4a6-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="2a4a6-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="2a4a6-119">[인수 개수를 확인 하는 방법을][]</span><span class="sxs-lookup"><span data-stu-id="2a4a6-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="2a4a6-120">[Writing a Windows PowerShell Cmdlet][](Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="2a4a6-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[인수 개수를 확인 하는 방법을]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md(Windows PowerShell Cmdlet 작성)

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
