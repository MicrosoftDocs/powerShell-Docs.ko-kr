---
title: View (Format)의 CustomControl 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363362"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="524b8-102">View에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="524b8-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="524b8-103">뷰의 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="524b8-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="524b8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="524b8-105">구문</span><span class="sxs-lookup"><span data-stu-id="524b8-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="524b8-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="524b8-106">Attributes and Elements</span></span>

<span data-ttu-id="524b8-107">다음 섹션에서는 특성, 자식 요소 및 `CustomControl` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="524b8-108">하나의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="524b8-109">특성</span><span class="sxs-lookup"><span data-stu-id="524b8-109">Attributes</span></span>

<span data-ttu-id="524b8-110">없음</span><span class="sxs-lookup"><span data-stu-id="524b8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="524b8-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="524b8-111">Child Elements</span></span>

|<span data-ttu-id="524b8-112">요소</span><span class="sxs-lookup"><span data-stu-id="524b8-112">Element</span></span>|<span data-ttu-id="524b8-113">설명</span><span class="sxs-lookup"><span data-stu-id="524b8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="524b8-114">CustomControl에 대 한 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="524b8-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="524b8-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-115">Required element.</span></span><br /><br /> <span data-ttu-id="524b8-116">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="524b8-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="524b8-117">Parent Elements</span></span>

|<span data-ttu-id="524b8-118">요소</span><span class="sxs-lookup"><span data-stu-id="524b8-118">Element</span></span>|<span data-ttu-id="524b8-119">설명</span><span class="sxs-lookup"><span data-stu-id="524b8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="524b8-120">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="524b8-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="524b8-121">하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="524b8-122">설명</span><span class="sxs-lookup"><span data-stu-id="524b8-122">Remarks</span></span>

<span data-ttu-id="524b8-123">대부분의 경우 각 컨트롤 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="524b8-124">이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="524b8-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="524b8-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="524b8-125">See Also</span></span>

[<span data-ttu-id="524b8-126">CustomControl에 대 한 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="524b8-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="524b8-127">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="524b8-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="524b8-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="524b8-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
