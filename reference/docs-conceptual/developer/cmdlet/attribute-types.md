---
title: 특성 유형 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 96fdd38ba10eb748ab0762f0c910463dd472494d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782381"
---
# <a name="attribute-types"></a><span data-ttu-id="f36fb-102">특성 유형</span><span class="sxs-lookup"><span data-stu-id="f36fb-102">Attribute Types</span></span>

<span data-ttu-id="f36fb-103">Cmdlet 특성은 기능별로 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="f36fb-104">다음 섹션에서는 사용 가능한 특성을 설명 하 고 특성이 호출 될 때 런타임이 수행 하는 작업을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="f36fb-105">Cmdlet 특성</span><span class="sxs-lookup"><span data-stu-id="f36fb-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="f36fb-106">cmdlet</span><span class="sxs-lookup"><span data-stu-id="f36fb-106">Cmdlet</span></span>

<span data-ttu-id="f36fb-107">.NET Framework 클래스를 cmdlet으로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="f36fb-108">필수 기본 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-108">This is the required base attribute.</span></span>
<span data-ttu-id="f36fb-109">자세한 내용은 [Cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="f36fb-110">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="f36fb-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="f36fb-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f36fb-111">Parameter</span></span>

<span data-ttu-id="f36fb-112">Cmdlet 클래스에서 공용 속성을 cmdlet 매개 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="f36fb-113">자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="f36fb-114">Alias</span><span class="sxs-lookup"><span data-stu-id="f36fb-114">Alias</span></span>

<span data-ttu-id="f36fb-115">매개 변수에 대 한 별칭을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="f36fb-116">자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="f36fb-117">인수 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="f36fb-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="f36fb-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f36fb-118">ValidateCount</span></span>

<span data-ttu-id="f36fb-119">Cmdlet 매개 변수에 사용할 수 있는 인수의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="f36fb-120">자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="f36fb-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="f36fb-121">ValidateLength</span></span>

<span data-ttu-id="f36fb-122">Cmdlet 매개 변수 인수에 대 한 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f36fb-123">자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="f36fb-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="f36fb-124">ValidatePattern</span></span>

<span data-ttu-id="f36fb-125">Cmdlet 매개 변수 인수가 일치 해야 하는 정규식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="f36fb-126">자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="f36fb-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f36fb-127">ValidateRange</span></span>

<span data-ttu-id="f36fb-128">Cmdlet 매개 변수 인수에 대 한 최소값 및 최대값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f36fb-129">자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="f36fb-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="f36fb-130">ValidateSet</span></span>

<span data-ttu-id="f36fb-131">Cmdlet 매개 변수 인수에 대 한 유효한 값 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f36fb-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="f36fb-132">자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f36fb-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f36fb-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f36fb-133">See Also</span></span>

[<span data-ttu-id="f36fb-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f36fb-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
