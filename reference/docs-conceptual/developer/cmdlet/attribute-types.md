---
title: 특성 유형 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364582"
---
# <a name="attribute-types"></a><span data-ttu-id="f7a2a-102">특성 유형</span><span class="sxs-lookup"><span data-stu-id="f7a2a-102">Attribute Types</span></span>

<span data-ttu-id="f7a2a-103">Cmdlet 특성은 기능별로 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="f7a2a-104">다음 섹션에서는 사용 가능한 특성을 설명 하 고 특성이 호출 될 때 런타임이 수행 하는 작업을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="f7a2a-105">Cmdlet 특성</span><span class="sxs-lookup"><span data-stu-id="f7a2a-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="f7a2a-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f7a2a-106">Cmdlet</span></span>

<span data-ttu-id="f7a2a-107">.NET Framework 클래스를 cmdlet으로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="f7a2a-108">필수 기본 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-108">This is the required base attribute.</span></span>
<span data-ttu-id="f7a2a-109">자세한 내용은 [Cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="f7a2a-110">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="f7a2a-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="f7a2a-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7a2a-111">Parameter</span></span>

<span data-ttu-id="f7a2a-112">Cmdlet 클래스에서 공용 속성을 cmdlet 매개 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="f7a2a-113">자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="f7a2a-114">별칭</span><span class="sxs-lookup"><span data-stu-id="f7a2a-114">Alias</span></span>

<span data-ttu-id="f7a2a-115">매개 변수에 대 한 별칭을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="f7a2a-116">자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="f7a2a-117">인수 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="f7a2a-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="f7a2a-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f7a2a-118">ValidateCount</span></span>

<span data-ttu-id="f7a2a-119">Cmdlet 매개 변수에 사용할 수 있는 인수의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="f7a2a-120">자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="f7a2a-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="f7a2a-121">ValidateLength</span></span>

<span data-ttu-id="f7a2a-122">Cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f7a2a-123">자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="f7a2a-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="f7a2a-124">ValidatePattern</span></span>

<span data-ttu-id="f7a2a-125">Cmdlet 매개 변수 인수가 일치 해야 하는 정규식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="f7a2a-126">자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="f7a2a-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f7a2a-127">ValidateRange</span></span>

<span data-ttu-id="f7a2a-128">Cmdlet 매개 변수 인수에 대 한 최소값 및 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f7a2a-129">자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="f7a2a-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="f7a2a-130">ValidateSet</span></span>

<span data-ttu-id="f7a2a-131">Cmdlet 매개 변수 인수에 대 한 유효한 값 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="f7a2a-132">자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a2a-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7a2a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7a2a-133">See Also</span></span>

[<span data-ttu-id="f7a2a-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f7a2a-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
