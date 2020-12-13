---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 Control에 대한 Name 요소(형식)
description: View에 대한 Controls의 Control에 대한 Name 요소(형식)
ms.openlocfilehash: 52b7170777a35596767c34f2d58106dfa6479567
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666487"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="c6f6b-103">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-103">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="c6f6b-104">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-104">Specifies the name of the control.</span></span>

<span data-ttu-id="c6f6b-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) Controls 요소에 대 한 컨트롤 요소 (format) 컨트롤 요소 (형식)의 컨트롤에 대 한 뷰 (format) Name 요소</span><span class="sxs-lookup"><span data-stu-id="c6f6b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c6f6b-106">구문</span><span class="sxs-lookup"><span data-stu-id="c6f6b-106">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6f6b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c6f6b-107">Attributes and Elements</span></span>

<span data-ttu-id="c6f6b-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="c6f6b-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c6f6b-109">특성</span><span class="sxs-lookup"><span data-stu-id="c6f6b-109">Attributes</span></span>

<span data-ttu-id="c6f6b-110">없음</span><span class="sxs-lookup"><span data-stu-id="c6f6b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c6f6b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c6f6b-111">Child Elements</span></span>

<span data-ttu-id="c6f6b-112">없음</span><span class="sxs-lookup"><span data-stu-id="c6f6b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c6f6b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c6f6b-113">Parent Elements</span></span>

|<span data-ttu-id="c6f6b-114">요소</span><span class="sxs-lookup"><span data-stu-id="c6f6b-114">Element</span></span>|<span data-ttu-id="c6f6b-115">설명</span><span class="sxs-lookup"><span data-stu-id="c6f6b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6f6b-116">보기에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-116">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="c6f6b-117">뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-117">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c6f6b-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="c6f6b-118">Text Value</span></span>

<span data-ttu-id="c6f6b-119">컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-119">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6f6b-120">설명</span><span class="sxs-lookup"><span data-stu-id="c6f6b-120">Remarks</span></span>

<span data-ttu-id="c6f6b-121">여기에 지정 된 이름은 다음 요소에서이 컨트롤을 참조 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="c6f6b-122">테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 만들 때 컨트롤은 [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md) 와 같은 요소로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="c6f6b-123">뷰에서 사용할 수 있는 다른 컨트롤을 만들 때 다음 요소를 사용 하 여이 컨트롤을 지정할 수 있습니다. [뷰 컨트롤의 CustomItem에 대 한 Expressionbinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-123">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c6f6b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6f6b-124">See Also</span></span>

[<span data-ttu-id="c6f6b-125">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c6f6b-126">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-126">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c6f6b-127">보기에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-127">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="c6f6b-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c6f6b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
