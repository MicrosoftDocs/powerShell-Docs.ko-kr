---
title: GroupBy (형식)의 CustomControl에 대 한 CustomEntries 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785951"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="9f30f-102">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f30f-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="9f30f-103">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-103">Provides the definitions for the control.</span></span> <span data-ttu-id="9f30f-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9f30f-105">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby 요소 (형식)의 경우 CustomControl에 대 한 CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="9f30f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f30f-106">구문</span><span class="sxs-lookup"><span data-stu-id="9f30f-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f30f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9f30f-107">Attributes and Elements</span></span>

<span data-ttu-id="9f30f-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntries` .</span><span class="sxs-lookup"><span data-stu-id="9f30f-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="9f30f-109">지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f30f-110">특성</span><span class="sxs-lookup"><span data-stu-id="9f30f-110">Attributes</span></span>

<span data-ttu-id="9f30f-111">없음</span><span class="sxs-lookup"><span data-stu-id="9f30f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f30f-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9f30f-112">Child Elements</span></span>

|<span data-ttu-id="9f30f-113">요소</span><span class="sxs-lookup"><span data-stu-id="9f30f-113">Element</span></span>|<span data-ttu-id="9f30f-114">설명</span><span class="sxs-lookup"><span data-stu-id="9f30f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f30f-115">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f30f-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="9f30f-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-116">Required element.</span></span><br /><br /> <span data-ttu-id="9f30f-117">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9f30f-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9f30f-118">Parent Elements</span></span>

|<span data-ttu-id="9f30f-119">요소</span><span class="sxs-lookup"><span data-stu-id="9f30f-119">Element</span></span>|<span data-ttu-id="9f30f-120">설명</span><span class="sxs-lookup"><span data-stu-id="9f30f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f30f-121">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f30f-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="9f30f-122">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f30f-123">설명</span><span class="sxs-lookup"><span data-stu-id="9f30f-123">Remarks</span></span>

<span data-ttu-id="9f30f-124">대부분의 경우 컨트롤에는 단일 요소에 지정 된 정의가 하나만 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="9f30f-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="9f30f-125">그러나 같은 컨트롤을 사용 하 여 다른 그룹을 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f30f-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="9f30f-126">이러한 경우 그룹의 요소를 정의할 수 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="9f30f-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f30f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f30f-127">See Also</span></span>

[<span data-ttu-id="9f30f-128">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f30f-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="9f30f-129">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f30f-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="9f30f-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9f30f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
