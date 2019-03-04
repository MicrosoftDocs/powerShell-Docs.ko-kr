---
title: TableControl (형식)에 대 한 EntrySelectedBy에 대 한 SelectionCondition TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856499"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e19c7-102">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e19c7-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e19c7-103">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="e19c7-104">이 형식은 존재 하는 경우 조건이 충족 되 고 테이블 행 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="e19c7-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소 TableRowEntry (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e19c7-106">구문</span><span class="sxs-lookup"><span data-stu-id="e19c7-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e19c7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-107">Attributes and Elements</span></span>

<span data-ttu-id="e19c7-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e19c7-109">특성</span><span class="sxs-lookup"><span data-stu-id="e19c7-109">Attributes</span></span>

<span data-ttu-id="e19c7-110">없음</span><span class="sxs-lookup"><span data-stu-id="e19c7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e19c7-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-111">Child Elements</span></span>

<span data-ttu-id="e19c7-112">없음</span><span class="sxs-lookup"><span data-stu-id="e19c7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e19c7-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-113">Parent Elements</span></span>

|<span data-ttu-id="e19c7-114">요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-114">Element</span></span>|<span data-ttu-id="e19c7-115">설명</span><span class="sxs-lookup"><span data-stu-id="e19c7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e19c7-116">TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e19c7-117">사용할 테이블 행이 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e19c7-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e19c7-118">Text Value</span></span>

<span data-ttu-id="e19c7-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e19c7-120">설명</span><span class="sxs-lookup"><span data-stu-id="e19c7-120">Remarks</span></span>

<span data-ttu-id="e19c7-121">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="e19c7-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e19c7-123">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e19c7-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e19c7-124">See Also</span></span>

[<span data-ttu-id="e19c7-125">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="e19c7-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e19c7-126">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e19c7-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e19c7-127">TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e19c7-128">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="e19c7-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e19c7-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e19c7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
