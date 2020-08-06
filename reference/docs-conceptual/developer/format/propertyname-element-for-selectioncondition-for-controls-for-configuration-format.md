---
title: 구성 (형식)의 컨트롤에 대 한 SelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7730951a840fcfcd8bf819fff5182049bd6b6c23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773133"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="c3765-102">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3765-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c3765-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3765-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c3765-104">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3765-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="c3765-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3765-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c3765-106">Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한의 Customentries 요소 구성 (형식) EntrySelectedBy 요소 구성 (형식)에 대 한 컨트롤에 대 한 customentries의 구성 (형식) PropertyName 요소에 대해 ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="c3765-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3765-107">구문</span><span class="sxs-lookup"><span data-stu-id="c3765-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3765-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c3765-108">Attributes and Elements</span></span>

<span data-ttu-id="c3765-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="c3765-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3765-110">특성</span><span class="sxs-lookup"><span data-stu-id="c3765-110">Attributes</span></span>

<span data-ttu-id="c3765-111">없음</span><span class="sxs-lookup"><span data-stu-id="c3765-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3765-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c3765-112">Child Elements</span></span>

<span data-ttu-id="c3765-113">없음</span><span class="sxs-lookup"><span data-stu-id="c3765-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3765-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c3765-114">Parent Elements</span></span>

|<span data-ttu-id="c3765-115">요소</span><span class="sxs-lookup"><span data-stu-id="c3765-115">Element</span></span>|<span data-ttu-id="c3765-116">설명</span><span class="sxs-lookup"><span data-stu-id="c3765-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3765-117">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3765-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="c3765-118">공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3765-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3765-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="c3765-119">Text Value</span></span>

<span data-ttu-id="c3765-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3765-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3765-121">설명</span><span class="sxs-lookup"><span data-stu-id="c3765-121">Remarks</span></span>

<span data-ttu-id="c3765-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3765-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="c3765-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3765-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3765-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3765-124">See Also</span></span>

[<span data-ttu-id="c3765-125">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3765-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="c3765-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c3765-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
