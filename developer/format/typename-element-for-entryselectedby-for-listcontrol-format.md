---
title: EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084031"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9fc2b-102">ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9fc2b-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9fc2b-103">이 항목의 목록 보기를 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="9fc2b-104">목록 항목에 대해 지정할 수 있는 형식의 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="9fc2b-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 TypeName 요소 ListEntry (형식)에 대 한 EntrySelectedBy ListControl (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="9fc2b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9fc2b-106">구문</span><span class="sxs-lookup"><span data-stu-id="9fc2b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fc2b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-107">Attributes and Elements</span></span>

<span data-ttu-id="9fc2b-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fc2b-109">특성</span><span class="sxs-lookup"><span data-stu-id="9fc2b-109">Attributes</span></span>

<span data-ttu-id="9fc2b-110">없음</span><span class="sxs-lookup"><span data-stu-id="9fc2b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9fc2b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-111">Child Elements</span></span>

<span data-ttu-id="9fc2b-112">없음</span><span class="sxs-lookup"><span data-stu-id="9fc2b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9fc2b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-113">Parent Elements</span></span>

|<span data-ttu-id="9fc2b-114">요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-114">Element</span></span>|<span data-ttu-id="9fc2b-115">설명</span><span class="sxs-lookup"><span data-stu-id="9fc2b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fc2b-116">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="9fc2b-117">이 목록 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9fc2b-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9fc2b-118">Text Value</span></span>

<span data-ttu-id="9fc2b-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9fc2b-120">설명</span><span class="sxs-lookup"><span data-stu-id="9fc2b-120">Remarks</span></span>

<span data-ttu-id="9fc2b-121">각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9fc2b-122">목록 보기에이 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9fc2b-123">예제</span><span class="sxs-lookup"><span data-stu-id="9fc2b-123">Example</span></span>

<span data-ttu-id="9fc2b-124">다음 예제에서는 선택 목록 뷰 항목에 대 한 세트를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc2b-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="9fc2b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fc2b-125">See Also</span></span>

[<span data-ttu-id="9fc2b-126">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="9fc2b-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9fc2b-127">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="9fc2b-128">ListEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="9fc2b-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9fc2b-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="9fc2b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
