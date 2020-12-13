---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)
description: Configuration에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)
ms.openlocfilehash: 3815956f59f19c0215aaf26b94dede656b9453cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648317"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="40054-103">Configuration에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-103">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="40054-104">공용 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40054-104">Specifies the name of a common control.</span></span> <span data-ttu-id="40054-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40054-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="40054-106">Configuration 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl for Configuration (Format) Customentries 요소 CustomControl 구성에 대 한 컨트롤의 경우 (Format) Customentries 요소 구성의 컨트롤에 대 한 customentries의 컨트롤에 대 한 customentries 요소 구성 (형식)에 대 한 컨트롤의 요소에 대 한 CustomControlName 요소 구성 (형식)</span><span class="sxs-lookup"><span data-stu-id="40054-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40054-107">구문</span><span class="sxs-lookup"><span data-stu-id="40054-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40054-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="40054-108">Attributes and Elements</span></span>

<span data-ttu-id="40054-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="40054-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40054-110">특성</span><span class="sxs-lookup"><span data-stu-id="40054-110">Attributes</span></span>

<span data-ttu-id="40054-111">없음</span><span class="sxs-lookup"><span data-stu-id="40054-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40054-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="40054-112">Child Elements</span></span>

<span data-ttu-id="40054-113">없음</span><span class="sxs-lookup"><span data-stu-id="40054-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40054-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="40054-114">Parent Elements</span></span>

|<span data-ttu-id="40054-115">요소</span><span class="sxs-lookup"><span data-stu-id="40054-115">Element</span></span>|<span data-ttu-id="40054-116">설명</span><span class="sxs-lookup"><span data-stu-id="40054-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40054-117">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-117">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="40054-118">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40054-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="40054-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="40054-119">Text Value</span></span>

<span data-ttu-id="40054-120">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40054-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="40054-121">설명</span><span class="sxs-lookup"><span data-stu-id="40054-121">Remarks</span></span>

<span data-ttu-id="40054-122">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40054-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="40054-123">다음 요소는 이러한 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40054-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="40054-124">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="40054-125">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="40054-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40054-126">See Also</span></span>

[<span data-ttu-id="40054-127">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="40054-128">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="40054-129">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40054-129">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="40054-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="40054-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
