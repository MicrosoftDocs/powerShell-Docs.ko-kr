---
title: SelectionSetName 요소 ViewSelectedBy (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858339"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="a0f67-102">ViewSelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a0f67-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="a0f67-103">보기에 표시 되는.NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="a0f67-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ViewSelectedBy 요소 (형식) SelectionSetName 요소 ViewSelectedBy (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="a0f67-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0f67-105">구문</span><span class="sxs-lookup"><span data-stu-id="a0f67-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0f67-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a0f67-106">Attributes and Elements</span></span>

<span data-ttu-id="a0f67-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0f67-108">특성</span><span class="sxs-lookup"><span data-stu-id="a0f67-108">Attributes</span></span>

<span data-ttu-id="a0f67-109">없음</span><span class="sxs-lookup"><span data-stu-id="a0f67-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0f67-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a0f67-110">Child Elements</span></span>

<span data-ttu-id="a0f67-111">없음</span><span class="sxs-lookup"><span data-stu-id="a0f67-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a0f67-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a0f67-112">Parent Elements</span></span>

|<span data-ttu-id="a0f67-113">요소</span><span class="sxs-lookup"><span data-stu-id="a0f67-113">Element</span></span>|<span data-ttu-id="a0f67-114">설명</span><span class="sxs-lookup"><span data-stu-id="a0f67-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0f67-115">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a0f67-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="a0f67-116">보기에 표시 되는.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a0f67-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="a0f67-117">Text Value</span></span>

<span data-ttu-id="a0f67-118">정의한 선택 세트의 이름을 지정 합니다 `Name` 선택 세트에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0f67-119">설명</span><span class="sxs-lookup"><span data-stu-id="a0f67-119">Remarks</span></span>

<span data-ttu-id="a0f67-120">상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a0f67-121">정의 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="a0f67-122">예제</span><span class="sxs-lookup"><span data-stu-id="a0f67-122">Example</span></span>

<span data-ttu-id="a0f67-123">다음 예제에서는 선택 목록 보기에 대 한 세트를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="a0f67-124">동일한 스키마는 테이블, 넓게 및 사용자 지정 보기에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0f67-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="a0f67-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0f67-125">See Also</span></span>

[<span data-ttu-id="a0f67-126">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="a0f67-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a0f67-127">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a0f67-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="a0f67-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="a0f67-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
