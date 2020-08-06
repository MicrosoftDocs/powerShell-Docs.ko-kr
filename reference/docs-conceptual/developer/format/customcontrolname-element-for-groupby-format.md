---
title: GroupBy (형식)에 대 한 CustomControlName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4e3102f12cd37fa72a2de1bf1db5d1f82db31222
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783741"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="4abfc-102">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="4abfc-103">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4abfc-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="4abfc-104">이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4abfc-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="4abfc-105">Configuration 요소 (Format) Viewcontrolelement (Format) View Element (format) GroupBy 요소 (GroupBy)의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4abfc-106">구문</span><span class="sxs-lookup"><span data-stu-id="4abfc-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4abfc-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4abfc-107">Attributes and Elements</span></span>

<span data-ttu-id="4abfc-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="4abfc-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4abfc-109">특성</span><span class="sxs-lookup"><span data-stu-id="4abfc-109">Attributes</span></span>

<span data-ttu-id="4abfc-110">없음</span><span class="sxs-lookup"><span data-stu-id="4abfc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4abfc-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4abfc-111">Child Elements</span></span>

<span data-ttu-id="4abfc-112">없음</span><span class="sxs-lookup"><span data-stu-id="4abfc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4abfc-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4abfc-113">Parent Elements</span></span>

|<span data-ttu-id="4abfc-114">요소</span><span class="sxs-lookup"><span data-stu-id="4abfc-114">Element</span></span>|<span data-ttu-id="4abfc-115">설명</span><span class="sxs-lookup"><span data-stu-id="4abfc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4abfc-116">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4abfc-117">Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4abfc-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4abfc-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4abfc-118">Text Value</span></span>

<span data-ttu-id="4abfc-119">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4abfc-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="4abfc-120">설명</span><span class="sxs-lookup"><span data-stu-id="4abfc-120">Remarks</span></span>

<span data-ttu-id="4abfc-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4abfc-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="4abfc-122">다음 요소는 이러한 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4abfc-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="4abfc-123">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="4abfc-124">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="4abfc-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4abfc-125">See Also</span></span>

[<span data-ttu-id="4abfc-126">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4abfc-127">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="4abfc-128">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4abfc-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4abfc-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4abfc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
