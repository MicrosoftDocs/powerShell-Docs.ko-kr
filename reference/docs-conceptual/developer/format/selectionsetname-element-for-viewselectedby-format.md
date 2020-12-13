---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy에 대한 SelectionSetName 요소(형식)
description: ViewSelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654913"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="68d68-103">ViewSelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="68d68-103">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="68d68-104">뷰에 표시 되는 .NET 개체의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68d68-104">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="68d68-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 ViewSelectedBy 요소 (format) SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="68d68-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68d68-106">구문</span><span class="sxs-lookup"><span data-stu-id="68d68-106">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68d68-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="68d68-107">Attributes and Elements</span></span>

<span data-ttu-id="68d68-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="68d68-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68d68-109">특성</span><span class="sxs-lookup"><span data-stu-id="68d68-109">Attributes</span></span>

<span data-ttu-id="68d68-110">없음</span><span class="sxs-lookup"><span data-stu-id="68d68-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68d68-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="68d68-111">Child Elements</span></span>

<span data-ttu-id="68d68-112">없음</span><span class="sxs-lookup"><span data-stu-id="68d68-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68d68-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="68d68-113">Parent Elements</span></span>

|<span data-ttu-id="68d68-114">요소</span><span class="sxs-lookup"><span data-stu-id="68d68-114">Element</span></span>|<span data-ttu-id="68d68-115">설명</span><span class="sxs-lookup"><span data-stu-id="68d68-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68d68-116">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="68d68-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="68d68-117">뷰에 표시 되는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="68d68-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="68d68-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="68d68-118">Text Value</span></span>

<span data-ttu-id="68d68-119">선택 집합의 요소에 정의 된 선택 집합의 이름을 지정 `Name` 합니다.</span><span class="sxs-lookup"><span data-stu-id="68d68-119">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="68d68-120">설명</span><span class="sxs-lookup"><span data-stu-id="68d68-120">Remarks</span></span>

<span data-ttu-id="68d68-121">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68d68-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="68d68-122">선택 집합 정의 및 참조에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68d68-122">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="68d68-123">예제</span><span class="sxs-lookup"><span data-stu-id="68d68-123">Example</span></span>

<span data-ttu-id="68d68-124">다음 예에서는 목록 뷰에 대 한 선택 집합을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="68d68-124">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="68d68-125">테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68d68-125">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="68d68-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68d68-126">See Also</span></span>

[<span data-ttu-id="68d68-127">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="68d68-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="68d68-128">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="68d68-128">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="68d68-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="68d68-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
