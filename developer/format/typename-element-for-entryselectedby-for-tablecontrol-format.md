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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855729"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2ee24-102">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2ee24-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2ee24-103">이 항목의 테이블 뷰를 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="2ee24-104">테이블 항목에 대해 지정할 수 있는 형식의 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="2ee24-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 (형식) TypeName 요소 EntrySelectedBy에 대 한 TableRowEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="2ee24-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ee24-106">구문</span><span class="sxs-lookup"><span data-stu-id="2ee24-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ee24-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2ee24-107">Attributes and Elements</span></span>

<span data-ttu-id="2ee24-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ee24-109">특성</span><span class="sxs-lookup"><span data-stu-id="2ee24-109">Attributes</span></span>

<span data-ttu-id="2ee24-110">없음</span><span class="sxs-lookup"><span data-stu-id="2ee24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ee24-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2ee24-111">Child Elements</span></span>

<span data-ttu-id="2ee24-112">없음</span><span class="sxs-lookup"><span data-stu-id="2ee24-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ee24-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2ee24-113">Parent Elements</span></span>

|<span data-ttu-id="2ee24-114">요소</span><span class="sxs-lookup"><span data-stu-id="2ee24-114">Element</span></span>|<span data-ttu-id="2ee24-115">설명</span><span class="sxs-lookup"><span data-stu-id="2ee24-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ee24-116">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2ee24-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2ee24-117">이 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ee24-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="2ee24-118">Text Value</span></span>

<span data-ttu-id="2ee24-119">.NET 유형 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ee24-120">설명</span><span class="sxs-lookup"><span data-stu-id="2ee24-120">Remarks</span></span>

<span data-ttu-id="2ee24-121">각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2ee24-122">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee24-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ee24-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ee24-123">See Also</span></span>

[<span data-ttu-id="2ee24-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="2ee24-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2ee24-125">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2ee24-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2ee24-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="2ee24-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
