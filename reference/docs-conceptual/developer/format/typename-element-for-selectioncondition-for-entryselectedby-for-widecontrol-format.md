---
title: WideControl (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783316"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="2d953-102">WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2d953-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="2d953-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d953-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="2d953-104">이 형식이 있으면 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d953-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="2d953-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionCondition 요소에 대해 WideEntry (형식)에 대 한 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="2d953-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d953-106">구문</span><span class="sxs-lookup"><span data-stu-id="2d953-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d953-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2d953-107">Attributes and Elements</span></span>

<span data-ttu-id="2d953-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="2d953-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d953-109">특성</span><span class="sxs-lookup"><span data-stu-id="2d953-109">Attributes</span></span>

<span data-ttu-id="2d953-110">없음</span><span class="sxs-lookup"><span data-stu-id="2d953-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d953-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2d953-111">Child Elements</span></span>

<span data-ttu-id="2d953-112">없음</span><span class="sxs-lookup"><span data-stu-id="2d953-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d953-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2d953-113">Parent Elements</span></span>

|<span data-ttu-id="2d953-114">요소</span><span class="sxs-lookup"><span data-stu-id="2d953-114">Element</span></span>|<span data-ttu-id="2d953-115">설명</span><span class="sxs-lookup"><span data-stu-id="2d953-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d953-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="2d953-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2d953-117">이 광범위 한 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d953-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2d953-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="2d953-118">Text Value</span></span>

<span data-ttu-id="2d953-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="2d953-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d953-120">설명</span><span class="sxs-lookup"><span data-stu-id="2d953-120">Remarks</span></span>

<span data-ttu-id="2d953-121">선택 조건은 .NET 유형 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d953-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="2d953-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d953-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2d953-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d953-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d953-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d953-124">See Also</span></span>

[<span data-ttu-id="2d953-125">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="2d953-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2d953-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="2d953-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2d953-127">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="2d953-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2d953-128">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2d953-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2d953-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2d953-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
