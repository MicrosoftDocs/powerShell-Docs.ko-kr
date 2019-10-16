---
title: 이 listcontrol (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361562"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d4804-102">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d4804-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d4804-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4804-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d4804-104">이 형식이 있으면 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4804-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="d4804-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 for ListEntries for이 listcontrol (format) EntrySelectedBy 요소 이 listcontrol에 대 한 EntrySelectedBy (형식)에 대 한이 listcontrol (Format) TypeName 요소에 대해 ListEntry for이 listcontrol (format) SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d4804-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4804-106">구문</span><span class="sxs-lookup"><span data-stu-id="d4804-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4804-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d4804-107">Attributes and Elements</span></span>

<span data-ttu-id="d4804-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4804-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4804-109">특성</span><span class="sxs-lookup"><span data-stu-id="d4804-109">Attributes</span></span>

<span data-ttu-id="d4804-110">없음</span><span class="sxs-lookup"><span data-stu-id="d4804-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4804-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d4804-111">Child Elements</span></span>

<span data-ttu-id="d4804-112">없음</span><span class="sxs-lookup"><span data-stu-id="d4804-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4804-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d4804-113">Parent Elements</span></span>

|<span data-ttu-id="d4804-114">요소</span><span class="sxs-lookup"><span data-stu-id="d4804-114">Element</span></span>|<span data-ttu-id="d4804-115">설명</span><span class="sxs-lookup"><span data-stu-id="d4804-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4804-116">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d4804-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d4804-117">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4804-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4804-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d4804-118">Text Value</span></span>

<span data-ttu-id="d4804-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4804-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4804-120">설명</span><span class="sxs-lookup"><span data-stu-id="d4804-120">Remarks</span></span>

<span data-ttu-id="d4804-121">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4804-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="d4804-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4804-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d4804-123">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4804-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4804-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4804-124">See Also</span></span>

[<span data-ttu-id="d4804-125">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d4804-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d4804-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="d4804-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d4804-127">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d4804-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d4804-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d4804-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
