---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)
description: ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: 2e8246e3ef2cba38824d8f8004acfffc3236df13
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645561"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="7c06a-103">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7c06a-103">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="7c06a-104">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c06a-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="7c06a-105">이 형식이 있으면 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c06a-105">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="7c06a-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for ListEntries (format) ListEntry Element for이 listcontrol (format) SelectionCondition 요소 for ListEntry (format) SelectionCondition 요소 for이 listcontrol (format) for EntrySelectedBy이 listcontrol (format)</span><span class="sxs-lookup"><span data-stu-id="7c06a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c06a-107">구문</span><span class="sxs-lookup"><span data-stu-id="7c06a-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c06a-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7c06a-108">Attributes and Elements</span></span>

<span data-ttu-id="7c06a-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="7c06a-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c06a-110">특성</span><span class="sxs-lookup"><span data-stu-id="7c06a-110">Attributes</span></span>

<span data-ttu-id="7c06a-111">없음</span><span class="sxs-lookup"><span data-stu-id="7c06a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c06a-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7c06a-112">Child Elements</span></span>

<span data-ttu-id="7c06a-113">없음</span><span class="sxs-lookup"><span data-stu-id="7c06a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7c06a-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7c06a-114">Parent Elements</span></span>

|<span data-ttu-id="7c06a-115">요소</span><span class="sxs-lookup"><span data-stu-id="7c06a-115">Element</span></span>|<span data-ttu-id="7c06a-116">설명</span><span class="sxs-lookup"><span data-stu-id="7c06a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c06a-117">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7c06a-117">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="7c06a-118">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c06a-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7c06a-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="7c06a-119">Text Value</span></span>

<span data-ttu-id="7c06a-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="7c06a-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c06a-121">설명</span><span class="sxs-lookup"><span data-stu-id="7c06a-121">Remarks</span></span>

<span data-ttu-id="7c06a-122">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c06a-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="7c06a-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c06a-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7c06a-124">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c06a-124">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7c06a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c06a-125">See Also</span></span>

[<span data-ttu-id="7c06a-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="7c06a-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7c06a-127">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="7c06a-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7c06a-128">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7c06a-128">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="7c06a-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="7c06a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
