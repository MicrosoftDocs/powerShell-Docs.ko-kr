---
title: GroupBy (형식)에 대 한 SelectionCondition TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858809"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="9d5d7-102">GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9d5d7-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="9d5d7-103">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9d5d7-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9d5d7-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry EntrySelectedBy SelectionCondition GroupBy (형식)에 대 한 TypeName 요소 GroupBy (형식)에 대 한 GroupBy (형식) SelectionCondition 요소에 대 한 GroupBy (형식) EntrySelectedBy 요소에</span><span class="sxs-lookup"><span data-stu-id="9d5d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d5d7-106">구문</span><span class="sxs-lookup"><span data-stu-id="9d5d7-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d5d7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9d5d7-107">Attributes and Elements</span></span>

<span data-ttu-id="9d5d7-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d5d7-109">특성</span><span class="sxs-lookup"><span data-stu-id="9d5d7-109">Attributes</span></span>

<span data-ttu-id="9d5d7-110">없음</span><span class="sxs-lookup"><span data-stu-id="9d5d7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d5d7-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9d5d7-111">Child Elements</span></span>

<span data-ttu-id="9d5d7-112">없음</span><span class="sxs-lookup"><span data-stu-id="9d5d7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d5d7-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9d5d7-113">Parent Elements</span></span>

|<span data-ttu-id="9d5d7-114">요소</span><span class="sxs-lookup"><span data-stu-id="9d5d7-114">Element</span></span>|<span data-ttu-id="9d5d7-115">설명</span><span class="sxs-lookup"><span data-stu-id="9d5d7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d5d7-116">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="9d5d7-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="9d5d7-117">사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d5d7-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9d5d7-118">Text Value</span></span>

<span data-ttu-id="9d5d7-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d5d7-120">설명</span><span class="sxs-lookup"><span data-stu-id="9d5d7-120">Remarks</span></span>

<span data-ttu-id="9d5d7-121">이 요소를 지정 하는 경우 지정할 수 없습니다는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="9d5d7-122">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9d5d7-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d5d7-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d5d7-123">See Also</span></span>

[<span data-ttu-id="9d5d7-124">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="9d5d7-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="9d5d7-125">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="9d5d7-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
