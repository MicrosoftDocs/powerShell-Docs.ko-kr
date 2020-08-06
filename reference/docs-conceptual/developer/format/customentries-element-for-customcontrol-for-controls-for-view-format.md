---
title: View 컨트롤의 CustomControl에 대 한 CustomEntries 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783707"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="2dead-102">View에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2dead-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="2dead-103">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-103">Provides the definitions for the control.</span></span> <span data-ttu-id="2dead-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2dead-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤의 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤 요소 (형식)에 대 한 CustomControl의 CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="2dead-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2dead-106">구문</span><span class="sxs-lookup"><span data-stu-id="2dead-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2dead-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2dead-107">Attributes and Elements</span></span>

<span data-ttu-id="2dead-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntries` .</span><span class="sxs-lookup"><span data-stu-id="2dead-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="2dead-109">지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="2dead-110">특성</span><span class="sxs-lookup"><span data-stu-id="2dead-110">Attributes</span></span>

<span data-ttu-id="2dead-111">없음</span><span class="sxs-lookup"><span data-stu-id="2dead-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2dead-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2dead-112">Child Elements</span></span>

|<span data-ttu-id="2dead-113">요소</span><span class="sxs-lookup"><span data-stu-id="2dead-113">Element</span></span>|<span data-ttu-id="2dead-114">설명</span><span class="sxs-lookup"><span data-stu-id="2dead-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2dead-115">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2dead-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="2dead-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-116">Required element.</span></span><br /><br /> <span data-ttu-id="2dead-117">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2dead-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2dead-118">Parent Elements</span></span>

|<span data-ttu-id="2dead-119">요소</span><span class="sxs-lookup"><span data-stu-id="2dead-119">Element</span></span>|<span data-ttu-id="2dead-120">설명</span><span class="sxs-lookup"><span data-stu-id="2dead-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2dead-121">View에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2dead-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="2dead-122">뷰에 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2dead-123">설명</span><span class="sxs-lookup"><span data-stu-id="2dead-123">Remarks</span></span>

<span data-ttu-id="2dead-124">대부분의 경우 컨트롤에는 단일 요소에 지정 된 정의가 하나만 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="2dead-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="2dead-125">그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="2dead-126">이러한 경우 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dead-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dead-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dead-127">See Also</span></span>

[<span data-ttu-id="2dead-128">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2dead-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="2dead-129">View에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2dead-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="2dead-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2dead-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
