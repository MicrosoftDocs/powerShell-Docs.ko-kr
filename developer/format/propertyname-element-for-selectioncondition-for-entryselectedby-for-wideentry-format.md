---
title: PropertyName 요소 EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860419"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="b3873-102">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b3873-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="b3873-103">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b3873-104">이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="b3873-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소에 대 한 WideEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소 WideEntry (형식)에</span><span class="sxs-lookup"><span data-stu-id="b3873-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3873-106">구문</span><span class="sxs-lookup"><span data-stu-id="b3873-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b3873-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b3873-107">Attributes and Elements</span></span>

<span data-ttu-id="b3873-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3873-109">특성</span><span class="sxs-lookup"><span data-stu-id="b3873-109">Attributes</span></span>

<span data-ttu-id="b3873-110">없음</span><span class="sxs-lookup"><span data-stu-id="b3873-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3873-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b3873-111">Child Elements</span></span>

<span data-ttu-id="b3873-112">없음</span><span class="sxs-lookup"><span data-stu-id="b3873-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b3873-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b3873-113">Parent Elements</span></span>

|<span data-ttu-id="b3873-114">요소</span><span class="sxs-lookup"><span data-stu-id="b3873-114">Element</span></span>|<span data-ttu-id="b3873-115">설명</span><span class="sxs-lookup"><span data-stu-id="b3873-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3873-116">WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b3873-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="b3873-117">이 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b3873-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b3873-118">Text Value</span></span>

<span data-ttu-id="b3873-119">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3873-120">설명</span><span class="sxs-lookup"><span data-stu-id="b3873-120">Remarks</span></span>

<span data-ttu-id="b3873-121">선택 조건 하나 이상의 속성 이름 또는 평가 수행 하려면 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b3873-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b3873-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [와이드 보기인 경우](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3873-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3873-124">See Also</span></span>

[<span data-ttu-id="b3873-125">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b3873-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b3873-126">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3873-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b3873-127">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="b3873-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b3873-128">WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b3873-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b3873-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="b3873-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
