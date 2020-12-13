---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)
description: Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648287"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="260e8-103">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="260e8-103">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="260e8-104">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-104">Provides a definition of the common control.</span></span> <span data-ttu-id="260e8-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="260e8-106">Configuration 요소 (format) 컨트롤 구성 요소에 대 한 Control 요소의 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) Customentries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식)</span><span class="sxs-lookup"><span data-stu-id="260e8-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="260e8-107">구문</span><span class="sxs-lookup"><span data-stu-id="260e8-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="260e8-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="260e8-108">Attributes and Elements</span></span>

<span data-ttu-id="260e8-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="260e8-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="260e8-110">정의에 표시 되는 항목을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-110">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="260e8-111">특성</span><span class="sxs-lookup"><span data-stu-id="260e8-111">Attributes</span></span>

<span data-ttu-id="260e8-112">없음</span><span class="sxs-lookup"><span data-stu-id="260e8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="260e8-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="260e8-113">Child Elements</span></span>

|<span data-ttu-id="260e8-114">요소</span><span class="sxs-lookup"><span data-stu-id="260e8-114">Element</span></span>|<span data-ttu-id="260e8-115">설명</span><span class="sxs-lookup"><span data-stu-id="260e8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="260e8-116">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="260e8-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="260e8-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="260e8-118">공용 컨트롤의 정의를 사용 하는 .NET 형식 또는이 컨트롤을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-118">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="260e8-119">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="260e8-119">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="260e8-120">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-120">Required element.</span></span><br /><br /> <span data-ttu-id="260e8-121">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-121">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="260e8-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="260e8-122">Parent Elements</span></span>

|<span data-ttu-id="260e8-123">요소</span><span class="sxs-lookup"><span data-stu-id="260e8-123">Element</span></span>|<span data-ttu-id="260e8-124">설명</span><span class="sxs-lookup"><span data-stu-id="260e8-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="260e8-125">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="260e8-125">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="260e8-126">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-126">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="260e8-127">설명</span><span class="sxs-lookup"><span data-stu-id="260e8-127">Remarks</span></span>

<span data-ttu-id="260e8-128">대부분의 경우 각 공용 사용자 지정 컨트롤에는 하나의 정의만 필요 하지만 동일한 컨트롤을 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-128">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="260e8-129">이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="260e8-129">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="260e8-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="260e8-130">See Also</span></span>

[<span data-ttu-id="260e8-131">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="260e8-131">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="260e8-132">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="260e8-132">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="260e8-133">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="260e8-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
