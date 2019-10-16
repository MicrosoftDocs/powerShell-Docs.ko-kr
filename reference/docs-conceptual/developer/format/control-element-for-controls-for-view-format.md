---
title: 보기에 대 한 컨트롤 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363472"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="a5eb7-102">View의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="a5eb7-103">뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="a5eb7-104">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5eb7-105">구문</span><span class="sxs-lookup"><span data-stu-id="a5eb7-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5eb7-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-106">Attributes and Elements</span></span>

<span data-ttu-id="a5eb7-107">다음 섹션에서는 `Control` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5eb7-108">특성</span><span class="sxs-lookup"><span data-stu-id="a5eb7-108">Attributes</span></span>

<span data-ttu-id="a5eb7-109">없음</span><span class="sxs-lookup"><span data-stu-id="a5eb7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5eb7-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-110">Child Elements</span></span>

|<span data-ttu-id="a5eb7-111">요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-111">Element</span></span>|<span data-ttu-id="a5eb7-112">설명</span><span class="sxs-lookup"><span data-stu-id="a5eb7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5eb7-113">View 컨트롤의 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="a5eb7-114">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-114">Required element.</span></span><br /><br /> <span data-ttu-id="a5eb7-115">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="a5eb7-116">View 컨트롤의 컨트롤에 대 한 CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="a5eb7-117">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-117">Required element.</span></span><br /><br /> <span data-ttu-id="a5eb7-118">이 뷰에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5eb7-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-119">Parent Elements</span></span>

|<span data-ttu-id="a5eb7-120">요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-120">Element</span></span>|<span data-ttu-id="a5eb7-121">설명</span><span class="sxs-lookup"><span data-stu-id="a5eb7-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5eb7-122">Controls 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="a5eb7-123">특정 뷰에서 사용할 수 있는 뷰 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5eb7-124">설명</span><span class="sxs-lookup"><span data-stu-id="a5eb7-124">Remarks</span></span>

<span data-ttu-id="a5eb7-125">이 컨트롤은 다음 요소로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5eb7-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="a5eb7-126">뷰의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="a5eb7-127">CustomControl에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="a5eb7-128">GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="a5eb7-129">GroupBy (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="a5eb7-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5eb7-130">See Also</span></span>

[<span data-ttu-id="a5eb7-131">View 컨트롤의 컨트롤에 대 한 CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a5eb7-132">뷰의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a5eb7-133">CustomControl에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a5eb7-134">GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="a5eb7-135">GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="a5eb7-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="a5eb7-136">Controls 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="a5eb7-137">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a5eb7-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a5eb7-138">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a5eb7-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
