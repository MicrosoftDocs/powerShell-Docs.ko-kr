---
title: WideControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856799"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="8aa68-102">WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8aa68-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="8aa68-103">정의 대 한.NET 개체 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="8aa68-104">정의는 이러한 개체 중 하나가 표시 될 때마다 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="8aa68-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소에 대 한 WideEntry (형식) SelectionSetName 요소에 대 한 EntrySelectedBy WideEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="8aa68-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8aa68-106">구문</span><span class="sxs-lookup"><span data-stu-id="8aa68-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8aa68-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8aa68-107">Attributes and Elements</span></span>

<span data-ttu-id="8aa68-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8aa68-109">특성</span><span class="sxs-lookup"><span data-stu-id="8aa68-109">Attributes</span></span>

<span data-ttu-id="8aa68-110">없음</span><span class="sxs-lookup"><span data-stu-id="8aa68-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8aa68-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8aa68-111">Child Elements</span></span>

<span data-ttu-id="8aa68-112">없음</span><span class="sxs-lookup"><span data-stu-id="8aa68-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8aa68-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8aa68-113">Parent Elements</span></span>

|<span data-ttu-id="8aa68-114">요소</span><span class="sxs-lookup"><span data-stu-id="8aa68-114">Element</span></span>|<span data-ttu-id="8aa68-115">설명</span><span class="sxs-lookup"><span data-stu-id="8aa68-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8aa68-116">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8aa68-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="8aa68-117">이 와이드 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8aa68-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="8aa68-118">Text Value</span></span>

<span data-ttu-id="8aa68-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8aa68-120">설명</span><span class="sxs-lookup"><span data-stu-id="8aa68-120">Remarks</span></span>

<span data-ttu-id="8aa68-121">각 정의 하나의 형식 이름, 선택 항목 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="8aa68-122">선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8aa68-123">예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8aa68-124">선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [정의 집합의 개체를 보려면](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8aa68-125">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa68-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8aa68-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8aa68-126">See Also</span></span>

[<span data-ttu-id="8aa68-127">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="8aa68-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8aa68-128">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="8aa68-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8aa68-129">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8aa68-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="8aa68-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="8aa68-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
