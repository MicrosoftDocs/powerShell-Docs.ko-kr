---
title: 구성 (형식)에 대 한 CustomControl의 CustomEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364072"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="73c69-102">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="73c69-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="73c69-103">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-103">Provides a definition of the common control.</span></span> <span data-ttu-id="73c69-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="73c69-105">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) 구성에 대 한 CustomControl의 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="73c69-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73c69-106">구문</span><span class="sxs-lookup"><span data-stu-id="73c69-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="73c69-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="73c69-107">Attributes and Elements</span></span>

<span data-ttu-id="73c69-108">다음 섹션에서는 특성, 자식 요소 및 `CustomEntry` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="73c69-109">정의에 표시 되는 항목을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="73c69-110">특성</span><span class="sxs-lookup"><span data-stu-id="73c69-110">Attributes</span></span>

<span data-ttu-id="73c69-111">없음</span><span class="sxs-lookup"><span data-stu-id="73c69-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73c69-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="73c69-112">Child Elements</span></span>

|<span data-ttu-id="73c69-113">요소</span><span class="sxs-lookup"><span data-stu-id="73c69-113">Element</span></span>|<span data-ttu-id="73c69-114">설명</span><span class="sxs-lookup"><span data-stu-id="73c69-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73c69-115">구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="73c69-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="73c69-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-116">Optional element.</span></span><br /><br /> <span data-ttu-id="73c69-117">공용 컨트롤의 정의를 사용 하는 .NET 형식 또는이 컨트롤을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="73c69-118">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="73c69-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="73c69-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-119">Required element.</span></span><br /><br /> <span data-ttu-id="73c69-120">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73c69-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="73c69-121">Parent Elements</span></span>

|<span data-ttu-id="73c69-122">요소</span><span class="sxs-lookup"><span data-stu-id="73c69-122">Element</span></span>|<span data-ttu-id="73c69-123">설명</span><span class="sxs-lookup"><span data-stu-id="73c69-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73c69-124">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="73c69-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="73c69-125">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73c69-126">설명</span><span class="sxs-lookup"><span data-stu-id="73c69-126">Remarks</span></span>

<span data-ttu-id="73c69-127">대부분의 경우 각 공용 사용자 지정 컨트롤에는 하나의 정의만 필요 하지만 동일한 컨트롤을 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="73c69-128">이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73c69-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="73c69-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73c69-129">See Also</span></span>

[<span data-ttu-id="73c69-130">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="73c69-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="73c69-131">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="73c69-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="73c69-132">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="73c69-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
