---
title: CustomControl 요소 보려면 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066671"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="3130b-102">View에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3130b-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="3130b-103">뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="3130b-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3130b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3130b-105">구문</span><span class="sxs-lookup"><span data-stu-id="3130b-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3130b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3130b-106">Attributes and Elements</span></span>

<span data-ttu-id="3130b-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControl` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="3130b-108">자식 요소가 하나를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3130b-109">특성</span><span class="sxs-lookup"><span data-stu-id="3130b-109">Attributes</span></span>

<span data-ttu-id="3130b-110">없음</span><span class="sxs-lookup"><span data-stu-id="3130b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3130b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3130b-111">Child Elements</span></span>

|<span data-ttu-id="3130b-112">요소</span><span class="sxs-lookup"><span data-stu-id="3130b-112">Element</span></span>|<span data-ttu-id="3130b-113">설명</span><span class="sxs-lookup"><span data-stu-id="3130b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3130b-114">뷰 (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="3130b-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="3130b-115">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-115">Required element.</span></span><br /><br /> <span data-ttu-id="3130b-116">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3130b-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3130b-117">Parent Elements</span></span>

|<span data-ttu-id="3130b-118">요소</span><span class="sxs-lookup"><span data-stu-id="3130b-118">Element</span></span>|<span data-ttu-id="3130b-119">설명</span><span class="sxs-lookup"><span data-stu-id="3130b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3130b-120">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3130b-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="3130b-121">하나 이상의.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3130b-122">설명</span><span class="sxs-lookup"><span data-stu-id="3130b-122">Remarks</span></span>

<span data-ttu-id="3130b-123">대부분의 경우에서 각 컨트롤 보기에 대 한 정의 하나만 필요 하지만 다른.NET 개체를 표시 하려면 같은 뷰를 사용 하려는 경우에 여러 정의 제공 하려면 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="3130b-124">이러한 경우 각 개체 또는 개체 집합에 대 한 별도 정의 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3130b-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3130b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3130b-125">See Also</span></span>

[<span data-ttu-id="3130b-126">뷰 (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="3130b-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3130b-127">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3130b-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="3130b-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="3130b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
