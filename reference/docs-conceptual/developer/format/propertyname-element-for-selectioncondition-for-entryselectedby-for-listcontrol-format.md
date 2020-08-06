---
title: 이 listcontrol (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3f0a6b6b381f39492da36dab271503fc7cf6e7fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785560"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="88c21-102">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="88c21-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="88c21-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88c21-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="88c21-104">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88c21-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="88c21-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy for ListEntry (format) PropertyName 요소에 대해 ListEntry (형식)에 대 한 SelectionCondition for (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="88c21-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88c21-106">구문</span><span class="sxs-lookup"><span data-stu-id="88c21-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88c21-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="88c21-107">Attributes and Elements</span></span>

<span data-ttu-id="88c21-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="88c21-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88c21-109">특성</span><span class="sxs-lookup"><span data-stu-id="88c21-109">Attributes</span></span>

<span data-ttu-id="88c21-110">없음</span><span class="sxs-lookup"><span data-stu-id="88c21-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88c21-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="88c21-111">Child Elements</span></span>

<span data-ttu-id="88c21-112">없음</span><span class="sxs-lookup"><span data-stu-id="88c21-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88c21-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="88c21-113">Parent Elements</span></span>

|<span data-ttu-id="88c21-114">요소</span><span class="sxs-lookup"><span data-stu-id="88c21-114">Element</span></span>|<span data-ttu-id="88c21-115">설명</span><span class="sxs-lookup"><span data-stu-id="88c21-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88c21-116">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="88c21-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="88c21-117">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="88c21-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88c21-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="88c21-118">Text Value</span></span>

<span data-ttu-id="88c21-119">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88c21-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="88c21-120">설명</span><span class="sxs-lookup"><span data-stu-id="88c21-120">Remarks</span></span>

<span data-ttu-id="88c21-121">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88c21-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="88c21-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88c21-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="88c21-123">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88c21-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88c21-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88c21-124">See Also</span></span>

[<span data-ttu-id="88c21-125">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="88c21-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="88c21-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="88c21-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="88c21-127">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="88c21-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="88c21-128">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="88c21-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="88c21-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="88c21-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
