---
title: GroupBy (형식)에 대 한 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e83ebd49e4f3087c817b3cc8772889dbe85113aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785611"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="dd295-102">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd295-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="dd295-103">값이 변경 될 때마다 새 그룹을 시작 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd295-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="dd295-104">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="dd295-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd295-105">구문</span><span class="sxs-lookup"><span data-stu-id="dd295-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd295-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="dd295-106">Attributes and Elements</span></span>

<span data-ttu-id="dd295-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="dd295-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd295-108">특성</span><span class="sxs-lookup"><span data-stu-id="dd295-108">Attributes</span></span>

<span data-ttu-id="dd295-109">없음</span><span class="sxs-lookup"><span data-stu-id="dd295-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd295-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="dd295-110">Child Elements</span></span>

<span data-ttu-id="dd295-111">없음</span><span class="sxs-lookup"><span data-stu-id="dd295-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd295-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="dd295-112">Parent Elements</span></span>

|<span data-ttu-id="dd295-113">요소</span><span class="sxs-lookup"><span data-stu-id="dd295-113">Element</span></span>|<span data-ttu-id="dd295-114">설명</span><span class="sxs-lookup"><span data-stu-id="dd295-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd295-115">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd295-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="dd295-116">.NET 개체 그룹이 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd295-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd295-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="dd295-117">Text Value</span></span>

<span data-ttu-id="dd295-118">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd295-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd295-119">설명</span><span class="sxs-lookup"><span data-stu-id="dd295-119">Remarks</span></span>

<span data-ttu-id="dd295-120">Windows PowerShell은이 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd295-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="dd295-121">이 요소를 지정 하면 새 그룹을 시작 하는 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd295-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="dd295-122">예제</span><span class="sxs-lookup"><span data-stu-id="dd295-122">Example</span></span>

<span data-ttu-id="dd295-123">다음 예제에서는 속성 값이 변경 될 때 새 그룹을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd295-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="dd295-124">이 요소를 포함 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd295-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd295-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd295-125">See Also</span></span>

[<span data-ttu-id="dd295-126">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd295-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="dd295-127">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd295-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="dd295-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="dd295-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
