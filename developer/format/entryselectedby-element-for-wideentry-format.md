---
title: EntrySelectedBy 요소 WideEntry (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854979"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="595ae-102">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="595ae-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="595ae-103">이 정의 된 와이드 보기인 경우 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="595ae-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소 WideEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="595ae-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="595ae-105">구문</span><span class="sxs-lookup"><span data-stu-id="595ae-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="595ae-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-106">Attributes and Elements</span></span>

<span data-ttu-id="595ae-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="595ae-108">특성</span><span class="sxs-lookup"><span data-stu-id="595ae-108">Attributes</span></span>

<span data-ttu-id="595ae-109">없음</span><span class="sxs-lookup"><span data-stu-id="595ae-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="595ae-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-110">Child Elements</span></span>

|<span data-ttu-id="595ae-111">요소</span><span class="sxs-lookup"><span data-stu-id="595ae-111">Element</span></span>|<span data-ttu-id="595ae-112">설명</span><span class="sxs-lookup"><span data-stu-id="595ae-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="595ae-113">WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="595ae-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-114">Optional element.</span></span><br /><br /> <span data-ttu-id="595ae-115">사용할이 넓은 보기 정의가 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="595ae-116">WideEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="595ae-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-117">Optional element.</span></span><br /><br /> <span data-ttu-id="595ae-118">이 넓은 보기 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="595ae-119">EntrySelectedBy WideEntry (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="595ae-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-120">Optional element.</span></span><br /><br /> <span data-ttu-id="595ae-121">이 넓은 보기 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="595ae-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-122">Parent Elements</span></span>

|<span data-ttu-id="595ae-123">요소</span><span class="sxs-lookup"><span data-stu-id="595ae-123">Element</span></span>|<span data-ttu-id="595ae-124">설명</span><span class="sxs-lookup"><span data-stu-id="595ae-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="595ae-125">WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="595ae-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="595ae-126">넓은 보기의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="595ae-127">설명</span><span class="sxs-lookup"><span data-stu-id="595ae-127">Remarks</span></span>

<span data-ttu-id="595ae-128">하나 이상의 형식, 선택 영역 집합 또는 와이드 뷰 정의 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="595ae-129">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="595ae-130">선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트 또는 특정 속성 값으로 계산 되는 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="595ae-131">선택 조건에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="595ae-132">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="595ae-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="595ae-133">See Also</span></span>

[<span data-ttu-id="595ae-134">WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="595ae-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="595ae-135">WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="595ae-136">WideEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="595ae-137">EntrySelectedBy WideEntry (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="595ae-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="595ae-138">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="595ae-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="595ae-139">데이터를 표시 하기 위한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="595ae-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="595ae-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="595ae-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
