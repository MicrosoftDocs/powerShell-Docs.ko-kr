---
title: WideControl (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 546225b0619ebec83d04a7e27bbc298ffef0a14d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785254"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="b8ed5-102">WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8ed5-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="b8ed5-103">정의에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="b8ed5-104">정의는 이러한 개체 중 하나가 표시 될 때마다 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="b8ed5-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionSetName 요소에 대해 WideEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="b8ed5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8ed5-106">구문</span><span class="sxs-lookup"><span data-stu-id="b8ed5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8ed5-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b8ed5-107">Attributes and Elements</span></span>

<span data-ttu-id="b8ed5-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="b8ed5-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8ed5-109">특성</span><span class="sxs-lookup"><span data-stu-id="b8ed5-109">Attributes</span></span>

<span data-ttu-id="b8ed5-110">없음</span><span class="sxs-lookup"><span data-stu-id="b8ed5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8ed5-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b8ed5-111">Child Elements</span></span>

<span data-ttu-id="b8ed5-112">없음</span><span class="sxs-lookup"><span data-stu-id="b8ed5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8ed5-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b8ed5-113">Parent Elements</span></span>

|<span data-ttu-id="b8ed5-114">요소</span><span class="sxs-lookup"><span data-stu-id="b8ed5-114">Element</span></span>|<span data-ttu-id="b8ed5-115">설명</span><span class="sxs-lookup"><span data-stu-id="b8ed5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8ed5-116">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8ed5-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="b8ed5-117">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b8ed5-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b8ed5-118">Text Value</span></span>

<span data-ttu-id="b8ed5-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8ed5-120">설명</span><span class="sxs-lookup"><span data-stu-id="b8ed5-120">Remarks</span></span>

<span data-ttu-id="b8ed5-121">각 정의는 하나의 유형 이름, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="b8ed5-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b8ed5-123">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b8ed5-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b8ed5-125">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8ed5-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8ed5-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8ed5-126">See Also</span></span>

[<span data-ttu-id="b8ed5-127">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b8ed5-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b8ed5-128">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="b8ed5-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b8ed5-129">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8ed5-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="b8ed5-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b8ed5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
