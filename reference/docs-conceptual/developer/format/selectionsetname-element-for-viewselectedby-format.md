---
title: ViewSelectedBy (형식)에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368262"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="3706d-102">ViewSelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3706d-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="3706d-103">뷰에 표시 되는 .NET 개체의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="3706d-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 ViewSelectedBy 요소 (format) SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3706d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3706d-105">구문</span><span class="sxs-lookup"><span data-stu-id="3706d-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3706d-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3706d-106">Attributes and Elements</span></span>

<span data-ttu-id="3706d-107">다음 섹션에서는 `SelectionSetName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3706d-108">특성</span><span class="sxs-lookup"><span data-stu-id="3706d-108">Attributes</span></span>

<span data-ttu-id="3706d-109">없음</span><span class="sxs-lookup"><span data-stu-id="3706d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3706d-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3706d-110">Child Elements</span></span>

<span data-ttu-id="3706d-111">없음</span><span class="sxs-lookup"><span data-stu-id="3706d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3706d-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3706d-112">Parent Elements</span></span>

|<span data-ttu-id="3706d-113">요소</span><span class="sxs-lookup"><span data-stu-id="3706d-113">Element</span></span>|<span data-ttu-id="3706d-114">설명</span><span class="sxs-lookup"><span data-stu-id="3706d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3706d-115">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3706d-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="3706d-116">뷰에 표시 되는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3706d-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3706d-117">Text Value</span></span>

<span data-ttu-id="3706d-118">선택 집합의 `Name` 요소로 정의 된 선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3706d-119">설명</span><span class="sxs-lookup"><span data-stu-id="3706d-119">Remarks</span></span>

<span data-ttu-id="3706d-120">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="3706d-121">선택 집합 정의 및 참조에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3706d-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3706d-122">예제</span><span class="sxs-lookup"><span data-stu-id="3706d-122">Example</span></span>

<span data-ttu-id="3706d-123">다음 예에서는 목록 뷰에 대 한 선택 집합을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="3706d-124">테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3706d-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="3706d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3706d-125">See Also</span></span>

[<span data-ttu-id="3706d-126">선택 집합 정의</span><span class="sxs-lookup"><span data-stu-id="3706d-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3706d-127">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3706d-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="3706d-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3706d-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
