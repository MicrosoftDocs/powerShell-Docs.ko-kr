---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)
description: Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: fddb8ddbac7c9292a05cadfa31f98db6439a557d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659676"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="5ea95-103">Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5ea95-103">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5ea95-104">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea95-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="5ea95-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea95-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5ea95-106">Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식) Customentries 요소 구성에 대 한 컨트롤 (형식) EntrySelectedBy 요소 구성 (형식)에 대 한 컨트롤에 대 한 customentries에 대 한 컨트롤에 대 한 Customentries에 대 한 컨트롤에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ea95-107">구문</span><span class="sxs-lookup"><span data-stu-id="5ea95-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ea95-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-108">Attributes and Elements</span></span>

<span data-ttu-id="5ea95-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="5ea95-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ea95-110">특성</span><span class="sxs-lookup"><span data-stu-id="5ea95-110">Attributes</span></span>

<span data-ttu-id="5ea95-111">없음</span><span class="sxs-lookup"><span data-stu-id="5ea95-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ea95-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-112">Child Elements</span></span>

<span data-ttu-id="5ea95-113">없음</span><span class="sxs-lookup"><span data-stu-id="5ea95-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ea95-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-114">Parent Elements</span></span>

|<span data-ttu-id="5ea95-115">요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-115">Element</span></span>|<span data-ttu-id="5ea95-116">설명</span><span class="sxs-lookup"><span data-stu-id="5ea95-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ea95-117">구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-117">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="5ea95-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea95-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ea95-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5ea95-119">Text Value</span></span>

<span data-ttu-id="5ea95-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="5ea95-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ea95-121">설명</span><span class="sxs-lookup"><span data-stu-id="5ea95-121">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5ea95-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ea95-122">See Also</span></span>

[<span data-ttu-id="5ea95-123">구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="5ea95-123">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="5ea95-124">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5ea95-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
