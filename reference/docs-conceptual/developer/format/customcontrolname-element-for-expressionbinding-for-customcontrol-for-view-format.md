---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)
description: View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666810"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="1086d-103">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-103">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="1086d-104">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1086d-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1086d-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1086d-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1086d-106">Configuration 요소 (Format) Viewcontrolelement (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) Customentries 요소의 view (format) customentries 요소에 대 한 customentries 요소 (view)의 customentries 요소 (형식)의 customentries 요소에 대 한 customentries 요소 (customentries의 경우)</span><span class="sxs-lookup"><span data-stu-id="1086d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1086d-107">구문</span><span class="sxs-lookup"><span data-stu-id="1086d-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1086d-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1086d-108">Attributes and Elements</span></span>

<span data-ttu-id="1086d-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="1086d-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1086d-110">특성</span><span class="sxs-lookup"><span data-stu-id="1086d-110">Attributes</span></span>

<span data-ttu-id="1086d-111">없음</span><span class="sxs-lookup"><span data-stu-id="1086d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1086d-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1086d-112">Child Elements</span></span>

<span data-ttu-id="1086d-113">없음</span><span class="sxs-lookup"><span data-stu-id="1086d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1086d-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1086d-114">Parent Elements</span></span>

|<span data-ttu-id="1086d-115">요소</span><span class="sxs-lookup"><span data-stu-id="1086d-115">Element</span></span>|<span data-ttu-id="1086d-116">설명</span><span class="sxs-lookup"><span data-stu-id="1086d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1086d-117">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-117">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1086d-118">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1086d-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1086d-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1086d-119">Text Value</span></span>

<span data-ttu-id="1086d-120">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1086d-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1086d-121">설명</span><span class="sxs-lookup"><span data-stu-id="1086d-121">Remarks</span></span>

<span data-ttu-id="1086d-122">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1086d-122">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1086d-123">이러한 컨트롤의 이름은 다음 요소로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1086d-123">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="1086d-124">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1086d-125">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1086d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1086d-126">See Also</span></span>

[<span data-ttu-id="1086d-127">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1086d-128">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1086d-129">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1086d-129">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1086d-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1086d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
