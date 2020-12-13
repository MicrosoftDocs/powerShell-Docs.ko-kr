---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy에 대한 CustomControlName 요소(형식)
description: GroupBy에 대한 CustomControlName 요소(형식)
ms.openlocfilehash: 03664fe4d5559312e2720a3892493c90c15f7501
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655415"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="fc476-103">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-103">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="fc476-104">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc476-104">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="fc476-105">이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc476-105">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="fc476-106">Configuration 요소 (Format) Viewcontrolelement (Format) View Element (format) GroupBy 요소 (GroupBy)의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc476-107">구문</span><span class="sxs-lookup"><span data-stu-id="fc476-107">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc476-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fc476-108">Attributes and Elements</span></span>

<span data-ttu-id="fc476-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="fc476-109">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc476-110">특성</span><span class="sxs-lookup"><span data-stu-id="fc476-110">Attributes</span></span>

<span data-ttu-id="fc476-111">없음</span><span class="sxs-lookup"><span data-stu-id="fc476-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc476-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fc476-112">Child Elements</span></span>

<span data-ttu-id="fc476-113">없음</span><span class="sxs-lookup"><span data-stu-id="fc476-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc476-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fc476-114">Parent Elements</span></span>

|<span data-ttu-id="fc476-115">요소</span><span class="sxs-lookup"><span data-stu-id="fc476-115">Element</span></span>|<span data-ttu-id="fc476-116">설명</span><span class="sxs-lookup"><span data-stu-id="fc476-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc476-117">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-117">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="fc476-118">Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc476-118">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc476-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="fc476-119">Text Value</span></span>

<span data-ttu-id="fc476-120">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc476-120">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc476-121">설명</span><span class="sxs-lookup"><span data-stu-id="fc476-121">Remarks</span></span>

<span data-ttu-id="fc476-122">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc476-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="fc476-123">다음 요소는 이러한 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc476-123">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="fc476-124">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="fc476-125">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="fc476-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc476-126">See Also</span></span>

[<span data-ttu-id="fc476-127">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="fc476-128">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-128">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="fc476-129">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc476-129">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="fc476-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fc476-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
