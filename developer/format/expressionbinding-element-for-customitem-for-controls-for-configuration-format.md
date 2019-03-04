---
title: ExpressionBinding 요소 구성 (형식)에 대 한 컨트롤에 대 한 CustomItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855139"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="0bea1-102">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0bea1-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0bea1-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="0bea1-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0bea1-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry CustomItem 구성 (형식)에 대 한 컨트롤에 대 한 구성 ExpressionBinding 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="0bea1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bea1-106">구문</span><span class="sxs-lookup"><span data-stu-id="0bea1-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0bea1-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-107">Attributes and Elements</span></span>

<span data-ttu-id="0bea1-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ExpressionBinding` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bea1-109">특성</span><span class="sxs-lookup"><span data-stu-id="0bea1-109">Attributes</span></span>

<span data-ttu-id="0bea1-110">없음</span><span class="sxs-lookup"><span data-stu-id="0bea1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bea1-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-111">Child Elements</span></span>

|<span data-ttu-id="0bea1-112">요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-112">Element</span></span>|<span data-ttu-id="0bea1-113">설명</span><span class="sxs-lookup"><span data-stu-id="0bea1-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="0bea1-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0bea1-115">이 컨트롤에서 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="0bea1-116">구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0bea1-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0bea1-118">공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="0bea1-119">구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0bea1-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0bea1-121">컬렉션의 요소는 컨트롤에서 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="0bea1-122">구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0bea1-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0bea1-124">이 공용 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="0bea1-125">구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0bea1-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-126">Optional element.</span></span><br /><br /> <span data-ttu-id="0bea1-127">공용 컨트롤에서 해당 값이 표시.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="0bea1-128">구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0bea1-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-129">Optional element.</span></span><br /><br /> <span data-ttu-id="0bea1-130">공용 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0bea1-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-131">Parent Elements</span></span>

|<span data-ttu-id="0bea1-132">요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-132">Element</span></span>|<span data-ttu-id="0bea1-133">설명</span><span class="sxs-lookup"><span data-stu-id="0bea1-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bea1-134">구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0bea1-135">사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bea1-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0bea1-136">설명</span><span class="sxs-lookup"><span data-stu-id="0bea1-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="0bea1-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bea1-137">See Also</span></span>

[<span data-ttu-id="0bea1-138">구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="0bea1-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bea1-139">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="0bea1-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
