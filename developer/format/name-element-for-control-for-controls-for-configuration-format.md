---
title: 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 요소 이름을 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065192"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="12236-102">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="12236-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="12236-103">컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12236-103">Specifies the name of the control.</span></span> <span data-ttu-id="12236-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12236-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="12236-105">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 Name 요소 (형식) 구성에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소</span><span class="sxs-lookup"><span data-stu-id="12236-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12236-106">구문</span><span class="sxs-lookup"><span data-stu-id="12236-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="12236-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="12236-107">Attributes and Elements</span></span>

<span data-ttu-id="12236-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Name` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12236-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12236-109">특성</span><span class="sxs-lookup"><span data-stu-id="12236-109">Attributes</span></span>

<span data-ttu-id="12236-110">없음</span><span class="sxs-lookup"><span data-stu-id="12236-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12236-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="12236-111">Child Elements</span></span>

<span data-ttu-id="12236-112">없음</span><span class="sxs-lookup"><span data-stu-id="12236-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12236-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="12236-113">Parent Elements</span></span>

|<span data-ttu-id="12236-114">요소</span><span class="sxs-lookup"><span data-stu-id="12236-114">Element</span></span>|<span data-ttu-id="12236-115">설명</span><span class="sxs-lookup"><span data-stu-id="12236-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12236-116">구성 (형식)에 대 한 컨트롤에 대 한 control 요소</span><span class="sxs-lookup"><span data-stu-id="12236-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="12236-117">컨트롤을 참조 하는 데 사용 되는 이름과 형식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12236-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="12236-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="12236-118">Text Value</span></span>

<span data-ttu-id="12236-119">이 컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12236-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="12236-120">설명</span><span class="sxs-lookup"><span data-stu-id="12236-120">Remarks</span></span>

<span data-ttu-id="12236-121">여기에 지정 된 이름은이 컨트롤을 참조 하는 다음 요소에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12236-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="12236-122">테이블, 목록, 와이드 또는 사용자 지정 컨트롤 뷰를 만들 때 다음 요소에서 컨트롤을 지정할 수 있습니다. [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="12236-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="12236-123">다른 공용 컨트롤을 만들 때이 컨트롤은 다음 요소로 지정할 수 있습니다. [구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="12236-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="12236-124">컨트롤을 만들 수 있습니다을 사용 하는 뷰를 하는 경우이 컨트롤은 다음 요소로 지정할 수 있습니다. [뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="12236-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="12236-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12236-125">See Also</span></span>

[<span data-ttu-id="12236-126">구성 (형식)에 대 한 컨트롤에 대 한 control 요소</span><span class="sxs-lookup"><span data-stu-id="12236-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="12236-127">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="12236-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="12236-128">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="12236-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="12236-129">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="12236-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="12236-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="12236-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
