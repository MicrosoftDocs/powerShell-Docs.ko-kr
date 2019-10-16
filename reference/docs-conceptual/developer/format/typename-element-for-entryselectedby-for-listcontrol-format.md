---
title: 이 listcontrol (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361662"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8f747-102">ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f747-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8f747-103">목록 뷰의이 항목을 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="8f747-104">목록 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="8f747-105">Configuration 요소 (Format) ViewDefinitions 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (형식) TypeName 요소 이 listcontrol에 대 한 EntrySelectedBy (형식)</span><span class="sxs-lookup"><span data-stu-id="8f747-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f747-106">구문</span><span class="sxs-lookup"><span data-stu-id="8f747-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f747-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8f747-107">Attributes and Elements</span></span>

<span data-ttu-id="8f747-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f747-109">특성</span><span class="sxs-lookup"><span data-stu-id="8f747-109">Attributes</span></span>

<span data-ttu-id="8f747-110">없음</span><span class="sxs-lookup"><span data-stu-id="8f747-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f747-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8f747-111">Child Elements</span></span>

<span data-ttu-id="8f747-112">없음</span><span class="sxs-lookup"><span data-stu-id="8f747-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f747-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8f747-113">Parent Elements</span></span>

|<span data-ttu-id="8f747-114">요소</span><span class="sxs-lookup"><span data-stu-id="8f747-114">Element</span></span>|<span data-ttu-id="8f747-115">설명</span><span class="sxs-lookup"><span data-stu-id="8f747-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f747-116">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8f747-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="8f747-117">이 목록 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f747-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="8f747-118">Text Value</span></span>

<span data-ttu-id="8f747-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f747-120">설명</span><span class="sxs-lookup"><span data-stu-id="8f747-120">Remarks</span></span>

<span data-ttu-id="8f747-121">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8f747-122">이 요소를 목록 뷰에서 사용 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f747-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8f747-123">예제</span><span class="sxs-lookup"><span data-stu-id="8f747-123">Example</span></span>

<span data-ttu-id="8f747-124">다음 예에서는 목록 뷰의 항목에 대해 선택 집합을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f747-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="8f747-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f747-125">See Also</span></span>

[<span data-ttu-id="8f747-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="8f747-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8f747-127">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8f747-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="8f747-128">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="8f747-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8f747-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8f747-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
