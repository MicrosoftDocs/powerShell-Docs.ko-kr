---
title: WideEntry (형식)에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363332"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="52148-102">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="52148-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="52148-103">이 정의를 사용 하기 위해 존재 해야 하는 조건 또는 넓은 뷰의이 정의를 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="52148-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="52148-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52148-105">구문</span><span class="sxs-lookup"><span data-stu-id="52148-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52148-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="52148-106">Attributes and Elements</span></span>

<span data-ttu-id="52148-107">다음 섹션에서는 특성, 자식 요소 및 `EntrySelectedBy` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52148-108">특성</span><span class="sxs-lookup"><span data-stu-id="52148-108">Attributes</span></span>

<span data-ttu-id="52148-109">없음</span><span class="sxs-lookup"><span data-stu-id="52148-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52148-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="52148-110">Child Elements</span></span>

|<span data-ttu-id="52148-111">요소</span><span class="sxs-lookup"><span data-stu-id="52148-111">Element</span></span>|<span data-ttu-id="52148-112">설명</span><span class="sxs-lookup"><span data-stu-id="52148-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52148-113">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="52148-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="52148-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52148-114">Optional element.</span></span><br /><br /> <span data-ttu-id="52148-115">이 광범위 한 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="52148-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="52148-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="52148-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52148-117">Optional element.</span></span><br /><br /> <span data-ttu-id="52148-118">이 넓은 뷰 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="52148-119">WideEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="52148-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="52148-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52148-120">Optional element.</span></span><br /><br /> <span data-ttu-id="52148-121">이 광범위 한 뷰 정의를 사용 하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52148-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="52148-122">Parent Elements</span></span>

|<span data-ttu-id="52148-123">요소</span><span class="sxs-lookup"><span data-stu-id="52148-123">Element</span></span>|<span data-ttu-id="52148-124">설명</span><span class="sxs-lookup"><span data-stu-id="52148-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52148-125">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="52148-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="52148-126">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52148-127">설명</span><span class="sxs-lookup"><span data-stu-id="52148-127">Remarks</span></span>

<span data-ttu-id="52148-128">넓은 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52148-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="52148-129">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52148-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="52148-130">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트 값이 `true`로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52148-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="52148-131">선택 조건에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52148-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="52148-132">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52148-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52148-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52148-133">See Also</span></span>

[<span data-ttu-id="52148-134">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="52148-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="52148-135">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="52148-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="52148-136">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="52148-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="52148-137">WideEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="52148-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="52148-138">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="52148-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="52148-139">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="52148-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="52148-140">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="52148-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
