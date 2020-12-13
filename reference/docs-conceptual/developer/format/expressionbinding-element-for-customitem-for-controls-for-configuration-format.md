---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)
description: Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655337"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="aacab-103">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-103">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="aacab-104">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="aacab-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="aacab-106">Configuration 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤의 요소 구성 (format) CustomControl 요소 구성 (형식)에 대 한 컨트롤의 Customentries 요소 구성에 대 한 컨트롤의 customentries 요소 구성 (format) Customentries 요소 구성 요소에 대 한 컨트롤의 Customentries에 대 한 컨트롤에 대 한 customentries 요소 구성 (형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aacab-107">구문</span><span class="sxs-lookup"><span data-stu-id="aacab-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="aacab-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="aacab-108">Attributes and Elements</span></span>

<span data-ttu-id="aacab-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="aacab-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aacab-110">특성</span><span class="sxs-lookup"><span data-stu-id="aacab-110">Attributes</span></span>

<span data-ttu-id="aacab-111">없음</span><span class="sxs-lookup"><span data-stu-id="aacab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aacab-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="aacab-112">Child Elements</span></span>

|<span data-ttu-id="aacab-113">요소</span><span class="sxs-lookup"><span data-stu-id="aacab-113">Element</span></span>|<span data-ttu-id="aacab-114">설명</span><span class="sxs-lookup"><span data-stu-id="aacab-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="aacab-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-115">Optional element.</span></span><br /><br /> <span data-ttu-id="aacab-116">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="aacab-117">Configuration에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-117">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aacab-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-118">Optional element.</span></span><br /><br /> <span data-ttu-id="aacab-119">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="aacab-120">Configuration에 대한 Controls의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-120">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aacab-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-121">Optional element.</span></span><br /><br /> <span data-ttu-id="aacab-122">컨트롤에서 컬렉션의 요소를 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-122">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="aacab-123">Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-123">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aacab-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-124">Optional element.</span></span><br /><br /> <span data-ttu-id="aacab-125">이 공용 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-125">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="aacab-126">Configuration에 대한 Controls의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-126">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aacab-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-127">Optional element.</span></span><br /><br /> <span data-ttu-id="aacab-128">공용 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-128">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="aacab-129">Configuration에 대한 Controls의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aacab-129">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="aacab-130">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-130">Optional element.</span></span><br /><br /> <span data-ttu-id="aacab-131">공용 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-131">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aacab-132">부모 요소</span><span class="sxs-lookup"><span data-stu-id="aacab-132">Parent Elements</span></span>

|<span data-ttu-id="aacab-133">요소</span><span class="sxs-lookup"><span data-stu-id="aacab-133">Element</span></span>|<span data-ttu-id="aacab-134">설명</span><span class="sxs-lookup"><span data-stu-id="aacab-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aacab-135">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="aacab-135">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="aacab-136">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aacab-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aacab-137">설명</span><span class="sxs-lookup"><span data-stu-id="aacab-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="aacab-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aacab-138">See Also</span></span>

[<span data-ttu-id="aacab-139">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="aacab-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="aacab-140">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="aacab-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
