---
title: TableControl (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361472"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="59f76-102">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="59f76-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="59f76-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f76-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="59f76-104">이 형식이 있으면 조건이 충족 되 고 테이블 행이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59f76-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="59f76-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (형식) TableRowEntry (형식)에 대 한 EntrySelectedBy에 대 한 TableRowEntry (Format) TypeName 요소의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59f76-106">구문</span><span class="sxs-lookup"><span data-stu-id="59f76-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59f76-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-107">Attributes and Elements</span></span>

<span data-ttu-id="59f76-108">다음 섹션에서는 특성, 자식 요소 및 `TypeName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f76-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="59f76-109">특성</span><span class="sxs-lookup"><span data-stu-id="59f76-109">Attributes</span></span>

<span data-ttu-id="59f76-110">없음</span><span class="sxs-lookup"><span data-stu-id="59f76-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59f76-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-111">Child Elements</span></span>

<span data-ttu-id="59f76-112">없음</span><span class="sxs-lookup"><span data-stu-id="59f76-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59f76-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-113">Parent Elements</span></span>

|<span data-ttu-id="59f76-114">요소</span><span class="sxs-lookup"><span data-stu-id="59f76-114">Element</span></span>|<span data-ttu-id="59f76-115">설명</span><span class="sxs-lookup"><span data-stu-id="59f76-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59f76-116">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="59f76-117">이 테이블 행을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f76-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="59f76-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="59f76-118">Text Value</span></span>

<span data-ttu-id="59f76-119">`System.IO.DirectoryInfo`와 같은 .NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="59f76-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="59f76-120">설명</span><span class="sxs-lookup"><span data-stu-id="59f76-120">Remarks</span></span>

<span data-ttu-id="59f76-121">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59f76-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="59f76-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59f76-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="59f76-123">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59f76-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59f76-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59f76-124">See Also</span></span>

[<span data-ttu-id="59f76-125">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="59f76-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="59f76-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="59f76-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="59f76-127">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="59f76-128">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="59f76-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="59f76-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="59f76-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
