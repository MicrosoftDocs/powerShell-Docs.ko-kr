---
title: View 컨트롤의 컨트롤에 대 한 Name 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365102"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="4a92b-102">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a92b-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="4a92b-103">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a92b-103">Specifies the name of the control.</span></span>

<span data-ttu-id="4a92b-104">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) Controls 요소에 대 한 컨트롤 요소 (format) 컨트롤 요소 (형식)의 컨트롤에 대 한 뷰 (format) Name 요소</span><span class="sxs-lookup"><span data-stu-id="4a92b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a92b-105">구문</span><span class="sxs-lookup"><span data-stu-id="4a92b-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a92b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4a92b-106">Attributes and Elements</span></span>

<span data-ttu-id="4a92b-107">다음 섹션에서는 `Name` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a92b-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a92b-108">특성</span><span class="sxs-lookup"><span data-stu-id="4a92b-108">Attributes</span></span>

<span data-ttu-id="4a92b-109">없음</span><span class="sxs-lookup"><span data-stu-id="4a92b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a92b-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4a92b-110">Child Elements</span></span>

<span data-ttu-id="4a92b-111">없음</span><span class="sxs-lookup"><span data-stu-id="4a92b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a92b-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4a92b-112">Parent Elements</span></span>

|<span data-ttu-id="4a92b-113">요소</span><span class="sxs-lookup"><span data-stu-id="4a92b-113">Element</span></span>|<span data-ttu-id="4a92b-114">설명</span><span class="sxs-lookup"><span data-stu-id="4a92b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a92b-115">보기에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a92b-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="4a92b-116">뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a92b-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4a92b-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4a92b-117">Text Value</span></span>

<span data-ttu-id="4a92b-118">컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a92b-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a92b-119">설명</span><span class="sxs-lookup"><span data-stu-id="4a92b-119">Remarks</span></span>

<span data-ttu-id="4a92b-120">여기에 지정 된 이름은 다음 요소에서이 컨트롤을 참조 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a92b-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="4a92b-121">테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 만들 때 컨트롤은 [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md) 와 같은 요소로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a92b-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="4a92b-122">뷰에서 사용할 수 있는 다른 컨트롤을 만들 때 다음 요소를 사용 하 여이 컨트롤을 지정할 수 있습니다. [뷰 컨트롤의 CustomItem에 대 한 Expressionbinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="4a92b-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="4a92b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a92b-123">See Also</span></span>

[<span data-ttu-id="4a92b-124">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a92b-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4a92b-125">뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a92b-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4a92b-126">보기에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a92b-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="4a92b-127">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4a92b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
