---
title: 뷰 (형식)에 대 한 CustomControl CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861699"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="bc057-102">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="bc057-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="bc057-103">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="bc057-104">사용자 지정 컨트롤 뷰는 하나 이상의 정의 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="bc057-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl 보려면 (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="bc057-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc057-106">구문</span><span class="sxs-lookup"><span data-stu-id="bc057-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc057-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-107">Attributes and Elements</span></span>

<span data-ttu-id="bc057-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControlEntries` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="bc057-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc057-110">특성</span><span class="sxs-lookup"><span data-stu-id="bc057-110">Attributes</span></span>

<span data-ttu-id="bc057-111">없음</span><span class="sxs-lookup"><span data-stu-id="bc057-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc057-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-112">Child Elements</span></span>

|<span data-ttu-id="bc057-113">요소</span><span class="sxs-lookup"><span data-stu-id="bc057-113">Element</span></span>|<span data-ttu-id="bc057-114">설명</span><span class="sxs-lookup"><span data-stu-id="bc057-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc057-115">뷰 (형식)에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="bc057-116">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-116">Required element.</span></span><br /><br /> <span data-ttu-id="bc057-117">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc057-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-118">Parent Elements</span></span>

|<span data-ttu-id="bc057-119">요소</span><span class="sxs-lookup"><span data-stu-id="bc057-119">Element</span></span>|<span data-ttu-id="bc057-120">설명</span><span class="sxs-lookup"><span data-stu-id="bc057-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc057-121">뷰 (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="bc057-122">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-122">Required element.</span></span><br /><br /> <span data-ttu-id="bc057-123">뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc057-124">설명</span><span class="sxs-lookup"><span data-stu-id="bc057-124">Remarks</span></span>

<span data-ttu-id="bc057-125">대부분의 경우 컨트롤에 단일에 정의 되어 있는 하나만 정의 `CustomEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="bc057-126">그러나는 다른.NET 개체를 표시 하려면 동일한 컨트롤을 사용 하려는 경우 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="bc057-127">이러한 경우에 정의할 수 있습니다는 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bc057-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc057-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc057-128">See Also</span></span>

[<span data-ttu-id="bc057-129">뷰 (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="bc057-130">뷰 (형식)에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="bc057-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="bc057-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="bc057-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
