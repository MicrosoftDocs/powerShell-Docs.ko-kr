---
title: View (Format)의 CustomControl에 대 한 CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364082"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="74208-102">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="74208-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="74208-103">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74208-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="74208-104">사용자 지정 컨트롤 뷰에서 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74208-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="74208-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="74208-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74208-106">구문</span><span class="sxs-lookup"><span data-stu-id="74208-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74208-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="74208-107">Attributes and Elements</span></span>

<span data-ttu-id="74208-108">다음 섹션에서는 `CustomControlEntries` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74208-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="74208-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74208-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="74208-110">특성</span><span class="sxs-lookup"><span data-stu-id="74208-110">Attributes</span></span>

<span data-ttu-id="74208-111">없음</span><span class="sxs-lookup"><span data-stu-id="74208-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74208-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="74208-112">Child Elements</span></span>

|<span data-ttu-id="74208-113">요소</span><span class="sxs-lookup"><span data-stu-id="74208-113">Element</span></span>|<span data-ttu-id="74208-114">설명</span><span class="sxs-lookup"><span data-stu-id="74208-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74208-115">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="74208-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="74208-116">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="74208-116">Required element.</span></span><br /><br /> <span data-ttu-id="74208-117">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74208-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="74208-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="74208-118">Parent Elements</span></span>

|<span data-ttu-id="74208-119">요소</span><span class="sxs-lookup"><span data-stu-id="74208-119">Element</span></span>|<span data-ttu-id="74208-120">설명</span><span class="sxs-lookup"><span data-stu-id="74208-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74208-121">보기에 대 한 CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="74208-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="74208-122">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="74208-122">Required element.</span></span><br /><br /> <span data-ttu-id="74208-123">뷰의 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="74208-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74208-124">설명</span><span class="sxs-lookup"><span data-stu-id="74208-124">Remarks</span></span>

<span data-ttu-id="74208-125">대부분의 경우 컨트롤에는 단일 `CustomEntry` 요소에 정의 된 정의가 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74208-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="74208-126">그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74208-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="74208-127">이러한 경우 각 개체 또는 개체 집합에 대 한 `CustomEntry` 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74208-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="74208-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74208-128">See Also</span></span>

[<span data-ttu-id="74208-129">보기에 대 한 CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="74208-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="74208-130">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="74208-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="74208-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="74208-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
