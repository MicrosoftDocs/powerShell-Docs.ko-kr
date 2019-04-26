---
title: GroupBy (형식)에 대 한 CustomControl CustomEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066488"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="55743-102">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="55743-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="55743-103">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="55743-103">Provides a definition of the control.</span></span> <span data-ttu-id="55743-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55743-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="55743-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식)에 대 한 CustomControl</span><span class="sxs-lookup"><span data-stu-id="55743-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55743-106">구문</span><span class="sxs-lookup"><span data-stu-id="55743-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55743-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="55743-107">Attributes and Elements</span></span>

<span data-ttu-id="55743-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55743-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55743-109">특성</span><span class="sxs-lookup"><span data-stu-id="55743-109">Attributes</span></span>

<span data-ttu-id="55743-110">없음</span><span class="sxs-lookup"><span data-stu-id="55743-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55743-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="55743-111">Child Elements</span></span>

|<span data-ttu-id="55743-112">요소</span><span class="sxs-lookup"><span data-stu-id="55743-112">Element</span></span>|<span data-ttu-id="55743-113">설명</span><span class="sxs-lookup"><span data-stu-id="55743-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55743-114">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="55743-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="55743-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55743-115">Optional element.</span></span><br /><br /> <span data-ttu-id="55743-116">이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="55743-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="55743-117">GroupBy (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="55743-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="55743-118">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55743-118">Required element.</span></span><br /><br /> <span data-ttu-id="55743-119">컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="55743-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="55743-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="55743-120">Parent Elements</span></span>

|<span data-ttu-id="55743-121">요소</span><span class="sxs-lookup"><span data-stu-id="55743-121">Element</span></span>|<span data-ttu-id="55743-122">설명</span><span class="sxs-lookup"><span data-stu-id="55743-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55743-123">GroupBy (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="55743-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="55743-124">컨트롤에 대 한 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="55743-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55743-125">설명</span><span class="sxs-lookup"><span data-stu-id="55743-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="55743-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55743-126">See Also</span></span>

[<span data-ttu-id="55743-127">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="55743-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="55743-128">GroupBy (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="55743-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="55743-129">GroupBy (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="55743-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="55743-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="55743-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
