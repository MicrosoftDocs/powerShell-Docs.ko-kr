---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651688"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ff915-103">WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ff915-103">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ff915-104">정의에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-104">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="ff915-105">정의는 이러한 개체 중 하나가 표시 될 때마다 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-105">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="ff915-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionSetName 요소에 대해 WideEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="ff915-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff915-107">구문</span><span class="sxs-lookup"><span data-stu-id="ff915-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff915-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ff915-108">Attributes and Elements</span></span>

<span data-ttu-id="ff915-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="ff915-109">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff915-110">특성</span><span class="sxs-lookup"><span data-stu-id="ff915-110">Attributes</span></span>

<span data-ttu-id="ff915-111">없음</span><span class="sxs-lookup"><span data-stu-id="ff915-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff915-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ff915-112">Child Elements</span></span>

<span data-ttu-id="ff915-113">없음</span><span class="sxs-lookup"><span data-stu-id="ff915-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ff915-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ff915-114">Parent Elements</span></span>

|<span data-ttu-id="ff915-115">요소</span><span class="sxs-lookup"><span data-stu-id="ff915-115">Element</span></span>|<span data-ttu-id="ff915-116">설명</span><span class="sxs-lookup"><span data-stu-id="ff915-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff915-117">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ff915-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="ff915-118">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ff915-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ff915-119">Text Value</span></span>

<span data-ttu-id="ff915-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff915-121">설명</span><span class="sxs-lookup"><span data-stu-id="ff915-121">Remarks</span></span>

<span data-ttu-id="ff915-122">각 정의는 하나의 유형 이름, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-122">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="ff915-123">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ff915-124">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff915-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ff915-125">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff915-125">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ff915-126">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff915-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff915-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff915-127">See Also</span></span>

[<span data-ttu-id="ff915-128">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ff915-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ff915-129">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="ff915-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ff915-130">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ff915-130">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="ff915-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ff915-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
