---
title: 구성 (형식)의 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3bfd3efe916b4d88c024de8f959482cab515f777
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781225"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="10d7e-102">Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="10d7e-103">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="10d7e-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="10d7e-105">Configuration 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl for Configuration (Format) Customentries 요소 CustomControl 구성에 대 한 컨트롤의 경우 (Format) Customentries 요소 구성의 컨트롤에 대 한 Customentries의 컨트롤에 대 한 customentries 요소 구성 (형식)에 대 한 컨트롤에 대 한 요소를 구성 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10d7e-106">구문</span><span class="sxs-lookup"><span data-stu-id="10d7e-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10d7e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="10d7e-107">Attributes and Elements</span></span>

<span data-ttu-id="10d7e-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="10d7e-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10d7e-109">특성</span><span class="sxs-lookup"><span data-stu-id="10d7e-109">Attributes</span></span>

<span data-ttu-id="10d7e-110">없음</span><span class="sxs-lookup"><span data-stu-id="10d7e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10d7e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="10d7e-111">Child Elements</span></span>

|<span data-ttu-id="10d7e-112">요소</span><span class="sxs-lookup"><span data-stu-id="10d7e-112">Element</span></span>|<span data-ttu-id="10d7e-113">설명</span><span class="sxs-lookup"><span data-stu-id="10d7e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10d7e-114">구성 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="10d7e-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="10d7e-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="10d7e-117">구성에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="10d7e-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="10d7e-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="10d7e-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="10d7e-120">Parent Elements</span></span>

|<span data-ttu-id="10d7e-121">요소</span><span class="sxs-lookup"><span data-stu-id="10d7e-121">Element</span></span>|<span data-ttu-id="10d7e-122">설명</span><span class="sxs-lookup"><span data-stu-id="10d7e-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10d7e-123">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="10d7e-124">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="10d7e-125">설명</span><span class="sxs-lookup"><span data-stu-id="10d7e-125">Remarks</span></span>

<span data-ttu-id="10d7e-126">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10d7e-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="10d7e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10d7e-127">See Also</span></span>

[<span data-ttu-id="10d7e-128">구성 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="10d7e-129">구성에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="10d7e-130">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="10d7e-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="10d7e-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="10d7e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
