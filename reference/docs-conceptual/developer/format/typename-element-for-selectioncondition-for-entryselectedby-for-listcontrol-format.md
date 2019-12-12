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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361562"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="3e1dd-102">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3e1dd-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="3e1dd-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="3e1dd-104">이 형식이 있으면 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="3e1dd-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 for ListEntries for이 listcontrol (format) EntrySelectedBy 요소 이 listcontrol에 대 한 EntrySelectedBy (형식)에 대 한이 listcontrol (Format) TypeName 요소에 대해 ListEntry for이 listcontrol (format) SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e1dd-106">구문</span><span class="sxs-lookup"><span data-stu-id="3e1dd-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e1dd-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-107">Attributes and Elements</span></span>

<span data-ttu-id="3e1dd-108">다음 섹션에서는 특성, 자식 요소 및 `TypeName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e1dd-109">특성</span><span class="sxs-lookup"><span data-stu-id="3e1dd-109">Attributes</span></span>

<span data-ttu-id="3e1dd-110">없음</span><span class="sxs-lookup"><span data-stu-id="3e1dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e1dd-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-111">Child Elements</span></span>

<span data-ttu-id="3e1dd-112">없음</span><span class="sxs-lookup"><span data-stu-id="3e1dd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e1dd-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-113">Parent Elements</span></span>

|<span data-ttu-id="3e1dd-114">요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-114">Element</span></span>|<span data-ttu-id="3e1dd-115">설명</span><span class="sxs-lookup"><span data-stu-id="3e1dd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e1dd-116">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3e1dd-117">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3e1dd-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3e1dd-118">Text Value</span></span>

<span data-ttu-id="3e1dd-119">`System.IO.DirectoryInfo`와 같은 .NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e1dd-120">설명</span><span class="sxs-lookup"><span data-stu-id="3e1dd-120">Remarks</span></span>

<span data-ttu-id="3e1dd-121">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="3e1dd-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3e1dd-123">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e1dd-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e1dd-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e1dd-124">See Also</span></span>

[<span data-ttu-id="3e1dd-125">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3e1dd-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3e1dd-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="3e1dd-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3e1dd-127">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="3e1dd-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3e1dd-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3e1dd-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
