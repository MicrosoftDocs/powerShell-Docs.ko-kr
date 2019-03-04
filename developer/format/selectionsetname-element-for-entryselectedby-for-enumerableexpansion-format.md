---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862749"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="d9d8a-102">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9d8a-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="d9d8a-103">이 정의 의해 확장 되는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="d9d8a-104">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionSetName 요소 EnumerableExpansion (형식)에 EnumerableExpansion (형식)</span><span class="sxs-lookup"><span data-stu-id="d9d8a-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9d8a-105">구문</span><span class="sxs-lookup"><span data-stu-id="d9d8a-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9d8a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d9d8a-106">Attributes and Elements</span></span>

<span data-ttu-id="d9d8a-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9d8a-108">특성</span><span class="sxs-lookup"><span data-stu-id="d9d8a-108">Attributes</span></span>

<span data-ttu-id="d9d8a-109">없음</span><span class="sxs-lookup"><span data-stu-id="d9d8a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9d8a-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d9d8a-110">Child Elements</span></span>

<span data-ttu-id="d9d8a-111">없음</span><span class="sxs-lookup"><span data-stu-id="d9d8a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9d8a-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d9d8a-112">Parent Elements</span></span>

|<span data-ttu-id="d9d8a-113">요소</span><span class="sxs-lookup"><span data-stu-id="d9d8a-113">Element</span></span>|<span data-ttu-id="d9d8a-114">설명</span><span class="sxs-lookup"><span data-stu-id="d9d8a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9d8a-115">EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="d9d8a-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="d9d8a-116">이 정의 의해 확장 되는.NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d9d8a-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d9d8a-117">Text Value</span></span>

<span data-ttu-id="d9d8a-118">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9d8a-119">설명</span><span class="sxs-lookup"><span data-stu-id="d9d8a-119">Remarks</span></span>

<span data-ttu-id="d9d8a-120">각 정의 하나 이상의 형식 이름, 집합을 선택 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="d9d8a-121">선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d9d8a-122">예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d9d8a-123">선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [정의 집합의 개체를 보려면](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d8a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9d8a-124">See Also</span></span>

[<span data-ttu-id="d9d8a-125">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="d9d8a-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d9d8a-126">EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="d9d8a-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="d9d8a-127">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d9d8a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
