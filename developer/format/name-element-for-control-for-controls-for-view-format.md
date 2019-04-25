---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 요소 이름을 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065106"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="3a514-102">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3a514-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="3a514-103">컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a514-103">Specifies the name of the control.</span></span>

<span data-ttu-id="3a514-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 요소 (형식)는 제어 (형식) 컨트롤 요소 컨트롤에 대 한 보기 (형식) 이름 요소에 대 한 컨트롤에 대 한 보기 (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="3a514-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a514-105">구문</span><span class="sxs-lookup"><span data-stu-id="3a514-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a514-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-106">Attributes and Elements</span></span>

<span data-ttu-id="3a514-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Name` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a514-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a514-108">특성</span><span class="sxs-lookup"><span data-stu-id="3a514-108">Attributes</span></span>

<span data-ttu-id="3a514-109">없음</span><span class="sxs-lookup"><span data-stu-id="3a514-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a514-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-110">Child Elements</span></span>

<span data-ttu-id="3a514-111">없음</span><span class="sxs-lookup"><span data-stu-id="3a514-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a514-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-112">Parent Elements</span></span>

|<span data-ttu-id="3a514-113">요소</span><span class="sxs-lookup"><span data-stu-id="3a514-113">Element</span></span>|<span data-ttu-id="3a514-114">설명</span><span class="sxs-lookup"><span data-stu-id="3a514-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a514-115">뷰 (형식)에 대 한 컨트롤에 대 한 control 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="3a514-116">보기 및 컨트롤을 참조 하는 데 사용 되는 이름으로 사용할 수 있는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a514-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3a514-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3a514-117">Text Value</span></span>

<span data-ttu-id="3a514-118">컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a514-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a514-119">설명</span><span class="sxs-lookup"><span data-stu-id="3a514-119">Remarks</span></span>

<span data-ttu-id="3a514-120">여기에 지정 된 이름은이 컨트롤을 참조 하는 다음 요소에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a514-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="3a514-121">테이블, 목록, 와이드 또는 사용자 지정 컨트롤 뷰를 만들 때 다음 요소에서 컨트롤을 지정할 수 있습니다. [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="3a514-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="3a514-122">다른 컨트롤을 만들 수 있습니다을 사용 하는 뷰일 경우이 컨트롤은 다음 요소로 지정할 수 있습니다. [뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="3a514-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="3a514-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a514-123">See Also</span></span>

[<span data-ttu-id="3a514-124">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3a514-125">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3a514-126">뷰 (형식)에 대 한 컨트롤에 대 한 control 요소</span><span class="sxs-lookup"><span data-stu-id="3a514-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="3a514-127">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="3a514-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
