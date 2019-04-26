---
title: TypeName 요소 EntrySelectedBy WideControl (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083810"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="795d4-102">WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="795d4-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="795d4-103">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="795d4-104">이 형식은 존재 하는 경우 정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="795d4-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소에 대 한 WideEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy SelectionCondition EntrySelectedBy WideEntry (형식)에 대 한에 대 한에 대 한 TypeName 요소의 WideEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="795d4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="795d4-106">구문</span><span class="sxs-lookup"><span data-stu-id="795d4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="795d4-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="795d4-107">Attributes and Elements</span></span>

<span data-ttu-id="795d4-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="795d4-109">특성</span><span class="sxs-lookup"><span data-stu-id="795d4-109">Attributes</span></span>

<span data-ttu-id="795d4-110">없음</span><span class="sxs-lookup"><span data-stu-id="795d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="795d4-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="795d4-111">Child Elements</span></span>

<span data-ttu-id="795d4-112">없음</span><span class="sxs-lookup"><span data-stu-id="795d4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="795d4-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="795d4-113">Parent Elements</span></span>

|<span data-ttu-id="795d4-114">요소</span><span class="sxs-lookup"><span data-stu-id="795d4-114">Element</span></span>|<span data-ttu-id="795d4-115">설명</span><span class="sxs-lookup"><span data-stu-id="795d4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="795d4-116">WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="795d4-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="795d4-117">사용할이 넓은 항목에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="795d4-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="795d4-118">Text Value</span></span>

<span data-ttu-id="795d4-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="795d4-120">설명</span><span class="sxs-lookup"><span data-stu-id="795d4-120">Remarks</span></span>

<span data-ttu-id="795d4-121">선택 조건에는.NET 형식을 지정할 수 또는 선택 영역을 설정 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="795d4-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="795d4-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="795d4-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="795d4-124">See Also</span></span>

[<span data-ttu-id="795d4-125">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="795d4-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="795d4-126">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="795d4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="795d4-127">WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="795d4-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="795d4-128">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="795d4-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="795d4-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="795d4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
