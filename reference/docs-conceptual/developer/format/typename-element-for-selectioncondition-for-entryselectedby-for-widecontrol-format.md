---
title: WideControl (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368062"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="eddab-102">WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="eddab-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="eddab-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eddab-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="eddab-104">이 형식이 있으면 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eddab-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="eddab-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) SelectionCondition 요소 WideEntry (형식)에 대 한 EntrySelectedBy에 대 한 WideEntry (Format) TypeName 요소의 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="eddab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eddab-106">구문</span><span class="sxs-lookup"><span data-stu-id="eddab-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eddab-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="eddab-107">Attributes and Elements</span></span>

<span data-ttu-id="eddab-108">다음 섹션에서는 특성, 자식 요소 및 `TypeName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eddab-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eddab-109">특성</span><span class="sxs-lookup"><span data-stu-id="eddab-109">Attributes</span></span>

<span data-ttu-id="eddab-110">없음</span><span class="sxs-lookup"><span data-stu-id="eddab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eddab-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="eddab-111">Child Elements</span></span>

<span data-ttu-id="eddab-112">없음</span><span class="sxs-lookup"><span data-stu-id="eddab-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eddab-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="eddab-113">Parent Elements</span></span>

|<span data-ttu-id="eddab-114">요소</span><span class="sxs-lookup"><span data-stu-id="eddab-114">Element</span></span>|<span data-ttu-id="eddab-115">설명</span><span class="sxs-lookup"><span data-stu-id="eddab-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eddab-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="eddab-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="eddab-117">이 광범위 한 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eddab-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eddab-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="eddab-118">Text Value</span></span>

<span data-ttu-id="eddab-119">`System.IO.DirectoryInfo`와 같은 .NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eddab-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="eddab-120">설명</span><span class="sxs-lookup"><span data-stu-id="eddab-120">Remarks</span></span>

<span data-ttu-id="eddab-121">선택 조건은 .NET 유형 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eddab-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="eddab-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eddab-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="eddab-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eddab-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eddab-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eddab-124">See Also</span></span>

[<span data-ttu-id="eddab-125">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="eddab-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="eddab-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="eddab-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="eddab-127">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="eddab-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="eddab-128">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="eddab-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="eddab-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="eddab-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
