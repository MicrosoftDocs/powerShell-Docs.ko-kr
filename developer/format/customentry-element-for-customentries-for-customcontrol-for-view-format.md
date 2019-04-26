---
title: CustomControl 보려면 (형식)에 대 한 CustomEntries CustomEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066450"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="00a89-102">View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="00a89-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="00a89-103">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="00a89-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="00a89-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00a89-105">구문</span><span class="sxs-lookup"><span data-stu-id="00a89-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00a89-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-106">Attributes and Elements</span></span>

<span data-ttu-id="00a89-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="00a89-108">정의 의해 표시 된 항목을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="00a89-109">특성</span><span class="sxs-lookup"><span data-stu-id="00a89-109">Attributes</span></span>

<span data-ttu-id="00a89-110">없음</span><span class="sxs-lookup"><span data-stu-id="00a89-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00a89-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-111">Child Elements</span></span>

|<span data-ttu-id="00a89-112">요소</span><span class="sxs-lookup"><span data-stu-id="00a89-112">Element</span></span>|<span data-ttu-id="00a89-113">설명</span><span class="sxs-lookup"><span data-stu-id="00a89-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00a89-114">뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="00a89-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-115">Optional element.</span></span><br /><br /> <span data-ttu-id="00a89-116">사용자 지정 컨트롤 뷰 또는이 정의를 사용할 수 있어야 하는 조건을 정의 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="00a89-117">뷰 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="00a89-118">사용자 지정 컨트롤 정의 대 한 컨트롤을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00a89-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-119">Parent Elements</span></span>

|<span data-ttu-id="00a89-120">요소</span><span class="sxs-lookup"><span data-stu-id="00a89-120">Element</span></span>|<span data-ttu-id="00a89-121">설명</span><span class="sxs-lookup"><span data-stu-id="00a89-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00a89-122">뷰 (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="00a89-123">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="00a89-124">사용자 지정 컨트롤 뷰는 하나 이상의 정의 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00a89-125">설명</span><span class="sxs-lookup"><span data-stu-id="00a89-125">Remarks</span></span>

<span data-ttu-id="00a89-126">대부분의 경우에서 하나만 정의 각 사용자 지정 컨트롤 보기에 대 한 필수 이지만 다른.NET 개체를 표시 하려면 같은 뷰를 사용 하려는 경우 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="00a89-127">이러한 경우 각 개체 또는 개체 집합에 대 한 별도 정의 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a89-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="00a89-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00a89-128">See Also</span></span>

[<span data-ttu-id="00a89-129">뷰 (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="00a89-130">뷰 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="00a89-131">뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="00a89-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="00a89-132">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="00a89-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
