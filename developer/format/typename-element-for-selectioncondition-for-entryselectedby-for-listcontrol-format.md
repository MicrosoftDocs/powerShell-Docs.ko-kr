---
title: TypeName 요소 EntrySelectedBy ListControl (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083861"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d1568-102">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d1568-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d1568-103">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d1568-104">이 형식이 있는 경우에 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="d1568-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntries ListControl (형식) EntrySelectedBy 요소에 대 한 (형식) ListControl ListEntry 요소에 ListEntry EntrySelectedBy SelectionCondition EntrySelectedBy ListControl (형식)에 대 한에 대 한 TypeName 요소 ListControl (형식)에 대 한 ListControl (형식) SelectionCondition 요소에</span><span class="sxs-lookup"><span data-stu-id="d1568-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1568-106">구문</span><span class="sxs-lookup"><span data-stu-id="d1568-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1568-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d1568-107">Attributes and Elements</span></span>

<span data-ttu-id="d1568-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1568-109">특성</span><span class="sxs-lookup"><span data-stu-id="d1568-109">Attributes</span></span>

<span data-ttu-id="d1568-110">없음</span><span class="sxs-lookup"><span data-stu-id="d1568-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1568-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d1568-111">Child Elements</span></span>

<span data-ttu-id="d1568-112">없음</span><span class="sxs-lookup"><span data-stu-id="d1568-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d1568-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d1568-113">Parent Elements</span></span>

|<span data-ttu-id="d1568-114">요소</span><span class="sxs-lookup"><span data-stu-id="d1568-114">Element</span></span>|<span data-ttu-id="d1568-115">설명</span><span class="sxs-lookup"><span data-stu-id="d1568-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1568-116">ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d1568-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d1568-117">사용할이 목록 항목에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d1568-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d1568-118">Text Value</span></span>

<span data-ttu-id="d1568-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1568-120">설명</span><span class="sxs-lookup"><span data-stu-id="d1568-120">Remarks</span></span>

<span data-ttu-id="d1568-121">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="d1568-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d1568-123">기타에 대 한 자세한 정보는 목록 보기의 구성 요소 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1568-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1568-124">See Also</span></span>

[<span data-ttu-id="d1568-125">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="d1568-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d1568-126">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1568-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d1568-127">ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d1568-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d1568-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d1568-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
