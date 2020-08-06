---
title: GroupBy (형식)에 대 한 SelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8ada9a8ca7fbfdba5b2fea1881b2670c56a71d4f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773082"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="a508d-102">GroupBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a508d-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="a508d-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a508d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a508d-104">이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a508d-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="a508d-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a508d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a508d-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl groupby (형식)에 대 한 CustomControl의 경우에는 groupby (형식)에 대 한 SelectionCondition 요소에 대해에 대 한</span><span class="sxs-lookup"><span data-stu-id="a508d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a508d-107">구문</span><span class="sxs-lookup"><span data-stu-id="a508d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a508d-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a508d-108">Attributes and Elements</span></span>

<span data-ttu-id="a508d-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="a508d-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a508d-110">특성</span><span class="sxs-lookup"><span data-stu-id="a508d-110">Attributes</span></span>

<span data-ttu-id="a508d-111">없음</span><span class="sxs-lookup"><span data-stu-id="a508d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a508d-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a508d-112">Child Elements</span></span>

<span data-ttu-id="a508d-113">없음</span><span class="sxs-lookup"><span data-stu-id="a508d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a508d-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a508d-114">Parent Elements</span></span>

|<span data-ttu-id="a508d-115">요소</span><span class="sxs-lookup"><span data-stu-id="a508d-115">Element</span></span>|<span data-ttu-id="a508d-116">설명</span><span class="sxs-lookup"><span data-stu-id="a508d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a508d-117">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a508d-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a508d-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a508d-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a508d-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="a508d-119">Text Value</span></span>

<span data-ttu-id="a508d-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a508d-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="a508d-121">설명</span><span class="sxs-lookup"><span data-stu-id="a508d-121">Remarks</span></span>

<span data-ttu-id="a508d-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a508d-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="a508d-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a508d-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a508d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a508d-124">See Also</span></span>

[<span data-ttu-id="a508d-125">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a508d-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="a508d-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a508d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
