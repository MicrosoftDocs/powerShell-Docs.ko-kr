---
ms.date: 09/13/2016
ms.topic: reference
title: View의 Controls에 대한 Control 요소(형식)
description: View의 Controls에 대한 Control 요소(형식)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668085"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="f2997-103">View의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-103">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="f2997-104">뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-104">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="f2997-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2997-106">구문</span><span class="sxs-lookup"><span data-stu-id="f2997-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2997-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f2997-107">Attributes and Elements</span></span>

<span data-ttu-id="f2997-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Control` .</span><span class="sxs-lookup"><span data-stu-id="f2997-108">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2997-109">특성</span><span class="sxs-lookup"><span data-stu-id="f2997-109">Attributes</span></span>

<span data-ttu-id="f2997-110">없음</span><span class="sxs-lookup"><span data-stu-id="f2997-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2997-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f2997-111">Child Elements</span></span>

|<span data-ttu-id="f2997-112">요소</span><span class="sxs-lookup"><span data-stu-id="f2997-112">Element</span></span>|<span data-ttu-id="f2997-113">설명</span><span class="sxs-lookup"><span data-stu-id="f2997-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2997-114">View 컨트롤의 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="f2997-114">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="f2997-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-115">Required element.</span></span><br /><br /> <span data-ttu-id="f2997-116">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-116">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="f2997-117">View에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-117">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="f2997-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-118">Required element.</span></span><br /><br /> <span data-ttu-id="f2997-119">이 뷰에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-119">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2997-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f2997-120">Parent Elements</span></span>

|<span data-ttu-id="f2997-121">요소</span><span class="sxs-lookup"><span data-stu-id="f2997-121">Element</span></span>|<span data-ttu-id="f2997-122">설명</span><span class="sxs-lookup"><span data-stu-id="f2997-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2997-123">Controls 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="f2997-123">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="f2997-124">특정 뷰에서 사용할 수 있는 뷰 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-124">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2997-125">설명</span><span class="sxs-lookup"><span data-stu-id="f2997-125">Remarks</span></span>

<span data-ttu-id="f2997-126">이 컨트롤은 다음 요소로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2997-126">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="f2997-127">View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-127">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="f2997-128">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-128">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="f2997-129">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-129">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="f2997-130">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-130">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="f2997-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2997-131">See Also</span></span>

[<span data-ttu-id="f2997-132">View에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-132">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f2997-133">View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-133">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="f2997-134">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-134">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f2997-135">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f2997-136">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-136">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f2997-137">Controls 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="f2997-137">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="f2997-138">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2997-138">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f2997-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f2997-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
