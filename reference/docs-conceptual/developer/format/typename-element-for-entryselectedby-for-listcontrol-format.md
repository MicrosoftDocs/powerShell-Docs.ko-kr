---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)
description: ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645660"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="34440-103">ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="34440-103">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="34440-104">목록 뷰의이 항목을 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34440-104">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="34440-105">목록 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34440-105">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="34440-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (형식) TypeName 요소에 대해이 listcontrol (형식)에 대해 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="34440-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34440-107">구문</span><span class="sxs-lookup"><span data-stu-id="34440-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34440-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="34440-108">Attributes and Elements</span></span>

<span data-ttu-id="34440-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="34440-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34440-110">특성</span><span class="sxs-lookup"><span data-stu-id="34440-110">Attributes</span></span>

<span data-ttu-id="34440-111">없음</span><span class="sxs-lookup"><span data-stu-id="34440-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34440-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="34440-112">Child Elements</span></span>

<span data-ttu-id="34440-113">없음</span><span class="sxs-lookup"><span data-stu-id="34440-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34440-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="34440-114">Parent Elements</span></span>

|<span data-ttu-id="34440-115">요소</span><span class="sxs-lookup"><span data-stu-id="34440-115">Element</span></span>|<span data-ttu-id="34440-116">설명</span><span class="sxs-lookup"><span data-stu-id="34440-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34440-117">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="34440-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="34440-118">이 목록 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="34440-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34440-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="34440-119">Text Value</span></span>

<span data-ttu-id="34440-120">같은 .NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo` 합니다.</span><span class="sxs-lookup"><span data-stu-id="34440-120">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="34440-121">설명</span><span class="sxs-lookup"><span data-stu-id="34440-121">Remarks</span></span>

<span data-ttu-id="34440-122">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34440-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="34440-123">이 요소를 목록 뷰에서 사용 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34440-123">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="34440-124">예제</span><span class="sxs-lookup"><span data-stu-id="34440-124">Example</span></span>

<span data-ttu-id="34440-125">다음 예에서는 목록 뷰의 항목에 대해 선택 집합을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34440-125">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="34440-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34440-126">See Also</span></span>

[<span data-ttu-id="34440-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="34440-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="34440-128">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="34440-128">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="34440-129">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="34440-129">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="34440-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="34440-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
