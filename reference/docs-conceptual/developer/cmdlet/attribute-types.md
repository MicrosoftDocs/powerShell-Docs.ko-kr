---
ms.date: 09/13/2016
ms.topic: reference
title: 특성 유형
description: 특성 유형
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667116"
---
# <a name="attribute-types"></a><span data-ttu-id="80eec-103">특성 유형</span><span class="sxs-lookup"><span data-stu-id="80eec-103">Attribute Types</span></span>

<span data-ttu-id="80eec-104">Cmdlet 특성은 기능별로 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-104">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="80eec-105">다음 섹션에서는 사용 가능한 특성을 설명 하 고 특성이 호출 될 때 런타임이 수행 하는 작업을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-105">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="80eec-106">Cmdlet 특성</span><span class="sxs-lookup"><span data-stu-id="80eec-106">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="80eec-107">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80eec-107">Cmdlet</span></span>

<span data-ttu-id="80eec-108">.NET Framework 클래스를 cmdlet으로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-108">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="80eec-109">필수 기본 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-109">This is the required base attribute.</span></span>
<span data-ttu-id="80eec-110">자세한 내용은 [Cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-110">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="80eec-111">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="80eec-111">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="80eec-112">매개 변수</span><span class="sxs-lookup"><span data-stu-id="80eec-112">Parameter</span></span>

<span data-ttu-id="80eec-113">Cmdlet 클래스에서 공용 속성을 cmdlet 매개 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-113">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="80eec-114">자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-114">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="80eec-115">Alias</span><span class="sxs-lookup"><span data-stu-id="80eec-115">Alias</span></span>

<span data-ttu-id="80eec-116">매개 변수에 대 한 별칭을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-116">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="80eec-117">자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-117">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="80eec-118">인수 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="80eec-118">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="80eec-119">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="80eec-119">ValidateCount</span></span>

<span data-ttu-id="80eec-120">Cmdlet 매개 변수에 사용할 수 있는 인수의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-120">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="80eec-121">자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-121">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="80eec-122">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="80eec-122">ValidateLength</span></span>

<span data-ttu-id="80eec-123">Cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-123">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="80eec-124">자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-124">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="80eec-125">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="80eec-125">ValidatePattern</span></span>

<span data-ttu-id="80eec-126">Cmdlet 매개 변수 인수가 일치 해야 하는 정규식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-126">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="80eec-127">자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-127">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="80eec-128">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="80eec-128">ValidateRange</span></span>

<span data-ttu-id="80eec-129">Cmdlet 매개 변수 인수에 대 한 최소값 및 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-129">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="80eec-130">자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-130">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="80eec-131">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="80eec-131">ValidateSet</span></span>

<span data-ttu-id="80eec-132">Cmdlet 매개 변수 인수에 대 한 유효한 값 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80eec-132">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="80eec-133">자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80eec-133">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80eec-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80eec-134">See Also</span></span>

[<span data-ttu-id="80eec-135">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="80eec-135">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
