---
title: GroupBy (형식)에 대 한 SelectionCondition의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361482"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="d39ec-102">GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d39ec-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="d39ec-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d39ec-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d39ec-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d39ec-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d39ec-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) EntrySelectedBy 요소에 대 한 CustomControl 요소에 대 한 CustomEntry for groupby (형식)에 대 한 selectioncondition 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="d39ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d39ec-106">구문</span><span class="sxs-lookup"><span data-stu-id="d39ec-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d39ec-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d39ec-107">Attributes and Elements</span></span>

<span data-ttu-id="d39ec-108">다음 섹션에서는 특성, 자식 요소 및 `TypeName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d39ec-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d39ec-109">특성</span><span class="sxs-lookup"><span data-stu-id="d39ec-109">Attributes</span></span>

<span data-ttu-id="d39ec-110">없음</span><span class="sxs-lookup"><span data-stu-id="d39ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d39ec-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d39ec-111">Child Elements</span></span>

<span data-ttu-id="d39ec-112">없음</span><span class="sxs-lookup"><span data-stu-id="d39ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d39ec-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d39ec-113">Parent Elements</span></span>

|<span data-ttu-id="d39ec-114">요소</span><span class="sxs-lookup"><span data-stu-id="d39ec-114">Element</span></span>|<span data-ttu-id="d39ec-115">설명</span><span class="sxs-lookup"><span data-stu-id="d39ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d39ec-116">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d39ec-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="d39ec-117">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d39ec-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d39ec-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d39ec-118">Text Value</span></span>

<span data-ttu-id="d39ec-119">`System.IO.DirectoryInfo`와 같은 .NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d39ec-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d39ec-120">설명</span><span class="sxs-lookup"><span data-stu-id="d39ec-120">Remarks</span></span>

<span data-ttu-id="d39ec-121">이 요소를 지정 하면 `SelectionSetName` 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d39ec-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="d39ec-122">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d39ec-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d39ec-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d39ec-123">See Also</span></span>

[<span data-ttu-id="d39ec-124">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d39ec-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="d39ec-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d39ec-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
