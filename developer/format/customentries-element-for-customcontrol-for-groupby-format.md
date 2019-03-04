---
title: GroupBy (형식)에 대 한 CustomControl CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853679"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="fa466-102">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fa466-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="fa466-103">컨트롤에 대 한 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-103">Provides the definitions for the control.</span></span> <span data-ttu-id="fa466-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fa466-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 GroupBy (형식)에 대 한 CustomControl CustomEntries 요소 GroupBy (형식)에 대 한 보기 (형식) CustomControl 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="fa466-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa466-106">구문</span><span class="sxs-lookup"><span data-stu-id="fa466-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa466-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-107">Attributes and Elements</span></span>

<span data-ttu-id="fa466-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomEntries` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="fa466-109">지정할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa466-110">특성</span><span class="sxs-lookup"><span data-stu-id="fa466-110">Attributes</span></span>

<span data-ttu-id="fa466-111">없음</span><span class="sxs-lookup"><span data-stu-id="fa466-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa466-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-112">Child Elements</span></span>

|<span data-ttu-id="fa466-113">요소</span><span class="sxs-lookup"><span data-stu-id="fa466-113">Element</span></span>|<span data-ttu-id="fa466-114">설명</span><span class="sxs-lookup"><span data-stu-id="fa466-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa466-115">GroupBy (형식)에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="fa466-116">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-116">Required element.</span></span><br /><br /> <span data-ttu-id="fa466-117">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fa466-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-118">Parent Elements</span></span>

|<span data-ttu-id="fa466-119">요소</span><span class="sxs-lookup"><span data-stu-id="fa466-119">Element</span></span>|<span data-ttu-id="fa466-120">설명</span><span class="sxs-lookup"><span data-stu-id="fa466-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa466-121">GroupBy (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="fa466-122">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fa466-123">설명</span><span class="sxs-lookup"><span data-stu-id="fa466-123">Remarks</span></span>

<span data-ttu-id="fa466-124">대부분의 경우 컨트롤에 단일에서 지정 되는 정의가 하나만 `CustomEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="fa466-125">그러나 동일한 컨트롤을 사용 하 여 다른 그룹을 표시 하려는 경우 여러 정의 제공 하는 것이 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="fa466-126">이러한 경우에 정의할 수 있습니다는 `CustomEntry` 그룹에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fa466-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa466-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa466-127">See Also</span></span>

[<span data-ttu-id="fa466-128">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="fa466-129">GroupBy (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="fa466-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="fa466-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="fa466-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
