---
title: 구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065514"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="ccf76-102">Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ccf76-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ccf76-103">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ccf76-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ccf76-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry CustomItem 구성 (형식)에 대 한 컨트롤에 대 한 구성 ExpressionBinding 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식) 구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccf76-106">구문</span><span class="sxs-lookup"><span data-stu-id="ccf76-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccf76-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-107">Attributes and Elements</span></span>

<span data-ttu-id="ccf76-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccf76-109">특성</span><span class="sxs-lookup"><span data-stu-id="ccf76-109">Attributes</span></span>

<span data-ttu-id="ccf76-110">없음</span><span class="sxs-lookup"><span data-stu-id="ccf76-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccf76-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-111">Child Elements</span></span>

|<span data-ttu-id="ccf76-112">요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-112">Element</span></span>|<span data-ttu-id="ccf76-113">설명</span><span class="sxs-lookup"><span data-stu-id="ccf76-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccf76-114">구성 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ccf76-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ccf76-116">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ccf76-117">구성 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ccf76-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ccf76-119">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ccf76-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-120">Parent Elements</span></span>

|<span data-ttu-id="ccf76-121">요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-121">Element</span></span>|<span data-ttu-id="ccf76-122">설명</span><span class="sxs-lookup"><span data-stu-id="ccf76-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccf76-123">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="ccf76-124">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ccf76-125">설명</span><span class="sxs-lookup"><span data-stu-id="ccf76-125">Remarks</span></span>

<span data-ttu-id="ccf76-126">하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccf76-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccf76-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccf76-127">See Also</span></span>

[<span data-ttu-id="ccf76-128">구성 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ccf76-129">구성 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ccf76-130">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="ccf76-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="ccf76-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="ccf76-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
