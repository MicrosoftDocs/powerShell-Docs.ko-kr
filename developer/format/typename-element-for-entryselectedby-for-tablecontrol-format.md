---
title: TableControl (형식)에 대 한 EntrySelectedBy TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083963"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e849b-102">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e849b-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e849b-103">이 항목의 테이블 뷰를 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="e849b-104">테이블 항목에 대해 지정할 수 있는 형식의 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="e849b-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 (형식) TypeName 요소 EntrySelectedBy에 대 한 TableRowEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="e849b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e849b-106">구문</span><span class="sxs-lookup"><span data-stu-id="e849b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e849b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e849b-107">Attributes and Elements</span></span>

<span data-ttu-id="e849b-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e849b-109">특성</span><span class="sxs-lookup"><span data-stu-id="e849b-109">Attributes</span></span>

<span data-ttu-id="e849b-110">없음</span><span class="sxs-lookup"><span data-stu-id="e849b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e849b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e849b-111">Child Elements</span></span>

<span data-ttu-id="e849b-112">없음</span><span class="sxs-lookup"><span data-stu-id="e849b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e849b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e849b-113">Parent Elements</span></span>

|<span data-ttu-id="e849b-114">요소</span><span class="sxs-lookup"><span data-stu-id="e849b-114">Element</span></span>|<span data-ttu-id="e849b-115">설명</span><span class="sxs-lookup"><span data-stu-id="e849b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e849b-116">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e849b-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e849b-117">이 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e849b-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e849b-118">Text Value</span></span>

<span data-ttu-id="e849b-119">.NET 유형 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="e849b-120">설명</span><span class="sxs-lookup"><span data-stu-id="e849b-120">Remarks</span></span>

<span data-ttu-id="e849b-121">각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e849b-122">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e849b-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e849b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e849b-123">See Also</span></span>

[<span data-ttu-id="e849b-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="e849b-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e849b-125">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e849b-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e849b-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e849b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
