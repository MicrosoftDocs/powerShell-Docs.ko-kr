---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)
description: GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)
ms.openlocfilehash: bb7dbd449137628da1794628c5a7d7e10158dd46
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655434"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="410d8-103">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-103">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="410d8-104">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="410d8-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="410d8-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl CustomControl for GroupBy (format) Customentries 요소에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 Customentries의 경우 groupby (형식)에 대 한 ExpressionBinding의 CustomControlName 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="410d8-107">구문</span><span class="sxs-lookup"><span data-stu-id="410d8-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="410d8-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="410d8-108">Attributes and Elements</span></span>

<span data-ttu-id="410d8-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="410d8-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="410d8-110">특성</span><span class="sxs-lookup"><span data-stu-id="410d8-110">Attributes</span></span>

<span data-ttu-id="410d8-111">없음</span><span class="sxs-lookup"><span data-stu-id="410d8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="410d8-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="410d8-112">Child Elements</span></span>

<span data-ttu-id="410d8-113">없음</span><span class="sxs-lookup"><span data-stu-id="410d8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="410d8-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="410d8-114">Parent Elements</span></span>

|<span data-ttu-id="410d8-115">요소</span><span class="sxs-lookup"><span data-stu-id="410d8-115">Element</span></span>|<span data-ttu-id="410d8-116">설명</span><span class="sxs-lookup"><span data-stu-id="410d8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="410d8-117">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-117">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="410d8-118">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="410d8-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="410d8-119">Text Value</span></span>

<span data-ttu-id="410d8-120">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="410d8-121">설명</span><span class="sxs-lookup"><span data-stu-id="410d8-121">Remarks</span></span>

<span data-ttu-id="410d8-122">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="410d8-123">다음 요소는 이러한 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="410d8-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="410d8-124">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="410d8-125">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="410d8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="410d8-126">See Also</span></span>

[<span data-ttu-id="410d8-127">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="410d8-128">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="410d8-129">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="410d8-129">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="410d8-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="410d8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
