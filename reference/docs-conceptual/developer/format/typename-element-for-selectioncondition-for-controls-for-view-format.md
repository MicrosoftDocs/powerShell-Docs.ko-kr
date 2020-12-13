---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)
description: View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: e70fc05667c27fa3b68f3c9a1802c1e3bba8b7ce
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651342"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="6e510-103">View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6e510-103">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="6e510-104">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e510-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="6e510-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e510-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6e510-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소입니다. view (format) EntrySelectedBy의 컨트롤에 대 한 CustomEntries 요소의 항목 요소에 대 한 참조 요소 뷰 (format)의 컨트롤에 대 한 SelectionCondition 요소에 대 한 컨트롤</span><span class="sxs-lookup"><span data-stu-id="6e510-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e510-107">구문</span><span class="sxs-lookup"><span data-stu-id="6e510-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e510-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6e510-108">Attributes and Elements</span></span>

<span data-ttu-id="6e510-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="6e510-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e510-110">특성</span><span class="sxs-lookup"><span data-stu-id="6e510-110">Attributes</span></span>

<span data-ttu-id="6e510-111">없음</span><span class="sxs-lookup"><span data-stu-id="6e510-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e510-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6e510-112">Child Elements</span></span>

<span data-ttu-id="6e510-113">없음</span><span class="sxs-lookup"><span data-stu-id="6e510-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6e510-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6e510-114">Parent Elements</span></span>

|<span data-ttu-id="6e510-115">요소</span><span class="sxs-lookup"><span data-stu-id="6e510-115">Element</span></span>|<span data-ttu-id="6e510-116">설명</span><span class="sxs-lookup"><span data-stu-id="6e510-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e510-117">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6e510-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6e510-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e510-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6e510-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6e510-119">Text Value</span></span>

<span data-ttu-id="6e510-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="6e510-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e510-121">설명</span><span class="sxs-lookup"><span data-stu-id="6e510-121">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6e510-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e510-122">See Also</span></span>

[<span data-ttu-id="6e510-123">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6e510-123">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="6e510-124">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6e510-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
