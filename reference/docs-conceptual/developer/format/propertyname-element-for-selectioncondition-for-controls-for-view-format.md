---
title: View 컨트롤의 SelectionCondition에 대 한 PropertyName 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 251fc129896cfa4a6255330e23854b014675ac5f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780817"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="1a791-102">View에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1a791-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="1a791-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1a791-104">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="1a791-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1a791-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소입니다. view (format) EntrySelectedBy의 컨트롤에 대 한 CustomEntries 요소의 항목 요소에 대 한 참조 요소 뷰 (format)의 컨트롤에 대 한 SelectionCondition 요소에 대 한 컨트롤의 SelectionCondition 요소에 대 한 컨트롤에 대 한 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a791-107">구문</span><span class="sxs-lookup"><span data-stu-id="1a791-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a791-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1a791-108">Attributes and Elements</span></span>

<span data-ttu-id="1a791-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="1a791-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a791-110">특성</span><span class="sxs-lookup"><span data-stu-id="1a791-110">Attributes</span></span>

<span data-ttu-id="1a791-111">없음</span><span class="sxs-lookup"><span data-stu-id="1a791-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a791-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1a791-112">Child Elements</span></span>

<span data-ttu-id="1a791-113">없음</span><span class="sxs-lookup"><span data-stu-id="1a791-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a791-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1a791-114">Parent Elements</span></span>

|<span data-ttu-id="1a791-115">요소</span><span class="sxs-lookup"><span data-stu-id="1a791-115">Element</span></span>|<span data-ttu-id="1a791-116">설명</span><span class="sxs-lookup"><span data-stu-id="1a791-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a791-117">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1a791-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="1a791-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1a791-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1a791-119">Text Value</span></span>

<span data-ttu-id="1a791-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a791-121">설명</span><span class="sxs-lookup"><span data-stu-id="1a791-121">Remarks</span></span>

<span data-ttu-id="1a791-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a791-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="1a791-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a791-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a791-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a791-124">See Also</span></span>

[<span data-ttu-id="1a791-125">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1a791-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="1a791-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1a791-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
