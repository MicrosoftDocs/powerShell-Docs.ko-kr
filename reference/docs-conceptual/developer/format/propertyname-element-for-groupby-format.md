---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy에 대한 PropertyName 요소(형식)
description: GroupBy에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666147"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="264ff-103">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="264ff-103">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="264ff-104">값이 변경 될 때마다 새 그룹을 시작 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="264ff-104">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="264ff-105">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="264ff-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="264ff-106">구문</span><span class="sxs-lookup"><span data-stu-id="264ff-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="264ff-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="264ff-107">Attributes and Elements</span></span>

<span data-ttu-id="264ff-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="264ff-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="264ff-109">특성</span><span class="sxs-lookup"><span data-stu-id="264ff-109">Attributes</span></span>

<span data-ttu-id="264ff-110">없음</span><span class="sxs-lookup"><span data-stu-id="264ff-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="264ff-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="264ff-111">Child Elements</span></span>

<span data-ttu-id="264ff-112">없음</span><span class="sxs-lookup"><span data-stu-id="264ff-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="264ff-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="264ff-113">Parent Elements</span></span>

|<span data-ttu-id="264ff-114">요소</span><span class="sxs-lookup"><span data-stu-id="264ff-114">Element</span></span>|<span data-ttu-id="264ff-115">설명</span><span class="sxs-lookup"><span data-stu-id="264ff-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="264ff-116">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="264ff-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="264ff-117">.NET 개체 그룹이 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="264ff-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="264ff-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="264ff-118">Text Value</span></span>

<span data-ttu-id="264ff-119">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="264ff-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="264ff-120">설명</span><span class="sxs-lookup"><span data-stu-id="264ff-120">Remarks</span></span>

<span data-ttu-id="264ff-121">Windows PowerShell은이 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="264ff-121">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="264ff-122">이 요소를 지정 하면 새 그룹을 시작 하는 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="264ff-122">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="264ff-123">예제</span><span class="sxs-lookup"><span data-stu-id="264ff-123">Example</span></span>

<span data-ttu-id="264ff-124">다음 예제에서는 속성 값이 변경 될 때 새 그룹을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="264ff-124">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="264ff-125">이 요소를 포함 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="264ff-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="264ff-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="264ff-126">See Also</span></span>

[<span data-ttu-id="264ff-127">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="264ff-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="264ff-128">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="264ff-128">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="264ff-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="264ff-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
