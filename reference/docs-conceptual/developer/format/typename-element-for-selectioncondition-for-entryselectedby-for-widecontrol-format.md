---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)
description: WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: af6e4782c345b43e16bce59c333bdaaceba0d845
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645500"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="dacf6-103">WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dacf6-103">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="dacf6-104">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dacf6-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="dacf6-105">이 형식이 있으면 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dacf6-105">When this type is present, the definition is used.</span></span>

<span data-ttu-id="dacf6-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionCondition 요소에 대해 WideEntry (형식)에 대 한 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dacf6-107">구문</span><span class="sxs-lookup"><span data-stu-id="dacf6-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dacf6-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-108">Attributes and Elements</span></span>

<span data-ttu-id="dacf6-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="dacf6-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dacf6-110">특성</span><span class="sxs-lookup"><span data-stu-id="dacf6-110">Attributes</span></span>

<span data-ttu-id="dacf6-111">없음</span><span class="sxs-lookup"><span data-stu-id="dacf6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dacf6-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-112">Child Elements</span></span>

<span data-ttu-id="dacf6-113">없음</span><span class="sxs-lookup"><span data-stu-id="dacf6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dacf6-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-114">Parent Elements</span></span>

|<span data-ttu-id="dacf6-115">요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-115">Element</span></span>|<span data-ttu-id="dacf6-116">설명</span><span class="sxs-lookup"><span data-stu-id="dacf6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dacf6-117">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="dacf6-118">이 광범위 한 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dacf6-118">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dacf6-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="dacf6-119">Text Value</span></span>

<span data-ttu-id="dacf6-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="dacf6-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="dacf6-121">설명</span><span class="sxs-lookup"><span data-stu-id="dacf6-121">Remarks</span></span>

<span data-ttu-id="dacf6-122">선택 조건은 .NET 유형 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dacf6-122">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="dacf6-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dacf6-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dacf6-124">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dacf6-124">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dacf6-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dacf6-125">See Also</span></span>

[<span data-ttu-id="dacf6-126">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="dacf6-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dacf6-127">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="dacf6-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dacf6-128">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="dacf6-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dacf6-129">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dacf6-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="dacf6-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="dacf6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
