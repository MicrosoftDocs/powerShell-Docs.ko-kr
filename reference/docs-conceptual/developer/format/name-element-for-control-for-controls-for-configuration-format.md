---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)
description: Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666504"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="9711e-103">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9711e-103">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9711e-104">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-104">Specifies the name of the control.</span></span> <span data-ttu-id="9711e-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9711e-106">구성 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤 요소 구성 (형식) 컨트롤의 요소 구성 (형식)에 대 한 컨트롤의 요소</span><span class="sxs-lookup"><span data-stu-id="9711e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9711e-107">구문</span><span class="sxs-lookup"><span data-stu-id="9711e-107">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9711e-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9711e-108">Attributes and Elements</span></span>

<span data-ttu-id="9711e-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="9711e-109">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9711e-110">특성</span><span class="sxs-lookup"><span data-stu-id="9711e-110">Attributes</span></span>

<span data-ttu-id="9711e-111">없음</span><span class="sxs-lookup"><span data-stu-id="9711e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9711e-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9711e-112">Child Elements</span></span>

<span data-ttu-id="9711e-113">없음</span><span class="sxs-lookup"><span data-stu-id="9711e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9711e-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9711e-114">Parent Elements</span></span>

|<span data-ttu-id="9711e-115">요소</span><span class="sxs-lookup"><span data-stu-id="9711e-115">Element</span></span>|<span data-ttu-id="9711e-116">설명</span><span class="sxs-lookup"><span data-stu-id="9711e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9711e-117">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9711e-117">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="9711e-118">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-118">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9711e-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9711e-119">Text Value</span></span>

<span data-ttu-id="9711e-120">이 컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-120">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9711e-121">설명</span><span class="sxs-lookup"><span data-stu-id="9711e-121">Remarks</span></span>

<span data-ttu-id="9711e-122">여기에 지정 된 이름은 다음 요소에서이 컨트롤을 참조 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-122">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="9711e-123">테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 만들 때 컨트롤은 [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md) 와 같은 요소로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-123">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="9711e-124">다른 공용 컨트롤을 만들 때이 컨트롤은 [구성 (형식)에 대 한 컨트롤의 CustomItem에 대 한 Expressionbinding 요소](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) 와 같은 요소로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9711e-124">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="9711e-125">뷰에서 사용할 수 있는 컨트롤을 만들 때이 컨트롤은 다음 요소를 사용 하 여 지정할 수 있습니다. [Expressionbinding 요소를 사용 하 여 뷰 컨트롤의 CustomItem에 대 한 요소입니다 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="9711e-125">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="9711e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9711e-126">See Also</span></span>

[<span data-ttu-id="9711e-127">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9711e-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="9711e-128">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9711e-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="9711e-129">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9711e-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="9711e-130">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9711e-130">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9711e-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9711e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
