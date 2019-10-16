---
title: GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368912"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="9a731-102">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9a731-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="9a731-103">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="9a731-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9a731-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 CustomControl에 대 한 customitem 요소에 대 한 customitem에 대 한 customitem에 대 한 CustomItem에 대 한 customitem의 경우 groupby (형식)에 대 한 ExpressionBinding의</span><span class="sxs-lookup"><span data-stu-id="9a731-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a731-106">구문</span><span class="sxs-lookup"><span data-stu-id="9a731-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a731-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9a731-107">Attributes and Elements</span></span>

<span data-ttu-id="9a731-108">다음 섹션에서는 `CustomControlName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a731-109">특성</span><span class="sxs-lookup"><span data-stu-id="9a731-109">Attributes</span></span>

<span data-ttu-id="9a731-110">없음</span><span class="sxs-lookup"><span data-stu-id="9a731-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a731-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9a731-111">Child Elements</span></span>

<span data-ttu-id="9a731-112">없음</span><span class="sxs-lookup"><span data-stu-id="9a731-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a731-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9a731-113">Parent Elements</span></span>

|<span data-ttu-id="9a731-114">요소</span><span class="sxs-lookup"><span data-stu-id="9a731-114">Element</span></span>|<span data-ttu-id="9a731-115">설명</span><span class="sxs-lookup"><span data-stu-id="9a731-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a731-116">GroupBy (형식)에 대 한 CustomItem의 ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="9a731-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="9a731-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a731-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9a731-118">Text Value</span></span>

<span data-ttu-id="9a731-119">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a731-120">설명</span><span class="sxs-lookup"><span data-stu-id="9a731-120">Remarks</span></span>

<span data-ttu-id="9a731-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="9a731-122">다음 요소는 이러한 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a731-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="9a731-123">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9a731-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="9a731-124">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="9a731-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="9a731-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a731-125">See Also</span></span>

[<span data-ttu-id="9a731-126">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9a731-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9a731-127">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="9a731-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="9a731-128">GroupBy (형식)에 대 한 CustomItem의 ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="9a731-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="9a731-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9a731-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
