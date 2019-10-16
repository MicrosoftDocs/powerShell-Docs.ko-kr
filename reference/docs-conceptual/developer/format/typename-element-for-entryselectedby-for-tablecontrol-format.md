---
title: TableControl (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361632"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2a30e-102">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2a30e-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2a30e-103">테이블 뷰의이 항목을 사용 하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a30e-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="2a30e-104">테이블 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a30e-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="2a30e-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소 (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format) TypeName 요소 TableRowEntry (형식)의 경우</span><span class="sxs-lookup"><span data-stu-id="2a30e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a30e-106">구문</span><span class="sxs-lookup"><span data-stu-id="2a30e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a30e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2a30e-107">Attributes and Elements</span></span>

<span data-ttu-id="2a30e-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a30e-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a30e-109">특성</span><span class="sxs-lookup"><span data-stu-id="2a30e-109">Attributes</span></span>

<span data-ttu-id="2a30e-110">없음</span><span class="sxs-lookup"><span data-stu-id="2a30e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a30e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2a30e-111">Child Elements</span></span>

<span data-ttu-id="2a30e-112">없음</span><span class="sxs-lookup"><span data-stu-id="2a30e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a30e-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2a30e-113">Parent Elements</span></span>

|<span data-ttu-id="2a30e-114">요소</span><span class="sxs-lookup"><span data-stu-id="2a30e-114">Element</span></span>|<span data-ttu-id="2a30e-115">설명</span><span class="sxs-lookup"><span data-stu-id="2a30e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a30e-116">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2a30e-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2a30e-117">이 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a30e-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a30e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="2a30e-118">Text Value</span></span>

<span data-ttu-id="2a30e-119">.NET 형식의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a30e-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a30e-120">설명</span><span class="sxs-lookup"><span data-stu-id="2a30e-120">Remarks</span></span>

<span data-ttu-id="2a30e-121">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a30e-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2a30e-122">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2a30e-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a30e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a30e-123">See Also</span></span>

[<span data-ttu-id="2a30e-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="2a30e-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2a30e-125">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2a30e-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2a30e-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2a30e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
