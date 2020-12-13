---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)
description: GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: 096d2355e113a7e44cc6ae31ea23efc3f01080a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664625"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="1875b-103">GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1875b-103">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="1875b-104">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1875b-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1875b-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1875b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1875b-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl groupby (형식)에 대 한 CustomControl의 경우에는 groupby (형식)에 대 한 SelectionCondition 요소에 대해 groupby (형식)에 대 한 Customentries 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="1875b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1875b-107">구문</span><span class="sxs-lookup"><span data-stu-id="1875b-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1875b-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1875b-108">Attributes and Elements</span></span>

<span data-ttu-id="1875b-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="1875b-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1875b-110">특성</span><span class="sxs-lookup"><span data-stu-id="1875b-110">Attributes</span></span>

<span data-ttu-id="1875b-111">없음</span><span class="sxs-lookup"><span data-stu-id="1875b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1875b-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1875b-112">Child Elements</span></span>

<span data-ttu-id="1875b-113">없음</span><span class="sxs-lookup"><span data-stu-id="1875b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1875b-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1875b-114">Parent Elements</span></span>

|<span data-ttu-id="1875b-115">요소</span><span class="sxs-lookup"><span data-stu-id="1875b-115">Element</span></span>|<span data-ttu-id="1875b-116">설명</span><span class="sxs-lookup"><span data-stu-id="1875b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1875b-117">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1875b-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1875b-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1875b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1875b-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1875b-119">Text Value</span></span>

<span data-ttu-id="1875b-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="1875b-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1875b-121">설명</span><span class="sxs-lookup"><span data-stu-id="1875b-121">Remarks</span></span>

<span data-ttu-id="1875b-122">이 요소를 지정 하면 요소를 지정할 수 없습니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="1875b-122">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="1875b-123">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1875b-123">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1875b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1875b-124">See Also</span></span>

[<span data-ttu-id="1875b-125">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1875b-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1875b-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1875b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
