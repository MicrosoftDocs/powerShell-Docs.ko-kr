---
title: GroupBy (형식)에 대 한 ExpressionBinding에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066571"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="b2633-102">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2633-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="b2633-103">공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="b2633-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b2633-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry CustomItem GroupBy (형식)에 대 한 ExpressionBinding CustomControlName 요소 GroupBy (형식)에 대 한 GroupBy (형식) ExpressionBinding 요소에 대 한 GroupBy (형식) CustomItem 요소에</span><span class="sxs-lookup"><span data-stu-id="b2633-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2633-106">구문</span><span class="sxs-lookup"><span data-stu-id="b2633-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2633-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-107">Attributes and Elements</span></span>

<span data-ttu-id="b2633-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControlName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2633-109">특성</span><span class="sxs-lookup"><span data-stu-id="b2633-109">Attributes</span></span>

<span data-ttu-id="b2633-110">없음</span><span class="sxs-lookup"><span data-stu-id="b2633-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2633-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-111">Child Elements</span></span>

<span data-ttu-id="b2633-112">없음</span><span class="sxs-lookup"><span data-stu-id="b2633-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2633-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-113">Parent Elements</span></span>

|<span data-ttu-id="b2633-114">요소</span><span class="sxs-lookup"><span data-stu-id="b2633-114">Element</span></span>|<span data-ttu-id="b2633-115">설명</span><span class="sxs-lookup"><span data-stu-id="b2633-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2633-116">GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b2633-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2633-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b2633-118">Text Value</span></span>

<span data-ttu-id="b2633-119">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2633-120">설명</span><span class="sxs-lookup"><span data-stu-id="b2633-120">Remarks</span></span>

<span data-ttu-id="b2633-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있습니다 하 고 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="b2633-122">다음 요소는 이러한 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2633-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="b2633-123">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="b2633-124">뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="b2633-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2633-125">See Also</span></span>

[<span data-ttu-id="b2633-126">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2633-127">뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b2633-128">GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="b2633-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b2633-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="b2633-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
