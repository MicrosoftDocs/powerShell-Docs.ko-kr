---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)
description: TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)
ms.openlocfilehash: 5a9f5cda1810d461d19ffb48a1cfa2d41f87ca96
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651423"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="dbf00-103">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dbf00-103">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="dbf00-104">테이블 뷰의이 항목을 사용 하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbf00-104">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="dbf00-105">테이블 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dbf00-105">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="dbf00-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (형식)에 대 한 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="dbf00-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dbf00-107">구문</span><span class="sxs-lookup"><span data-stu-id="dbf00-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbf00-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="dbf00-108">Attributes and Elements</span></span>

<span data-ttu-id="dbf00-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="dbf00-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbf00-110">특성</span><span class="sxs-lookup"><span data-stu-id="dbf00-110">Attributes</span></span>

<span data-ttu-id="dbf00-111">없음</span><span class="sxs-lookup"><span data-stu-id="dbf00-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dbf00-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="dbf00-112">Child Elements</span></span>

<span data-ttu-id="dbf00-113">없음</span><span class="sxs-lookup"><span data-stu-id="dbf00-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbf00-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="dbf00-114">Parent Elements</span></span>

|<span data-ttu-id="dbf00-115">요소</span><span class="sxs-lookup"><span data-stu-id="dbf00-115">Element</span></span>|<span data-ttu-id="dbf00-116">설명</span><span class="sxs-lookup"><span data-stu-id="dbf00-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbf00-117">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="dbf00-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="dbf00-118">이 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbf00-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dbf00-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="dbf00-119">Text Value</span></span>

<span data-ttu-id="dbf00-120">.NET 형식의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbf00-120">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbf00-121">설명</span><span class="sxs-lookup"><span data-stu-id="dbf00-121">Remarks</span></span>

<span data-ttu-id="dbf00-122">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbf00-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dbf00-123">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dbf00-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbf00-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbf00-124">See Also</span></span>

[<span data-ttu-id="dbf00-125">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="dbf00-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="dbf00-126">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="dbf00-126">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="dbf00-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="dbf00-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
