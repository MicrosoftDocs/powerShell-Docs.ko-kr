---
title: GroupBy (형식)에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368882"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="4ec91-102">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4ec91-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="4ec91-103">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="4ec91-104">이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="4ec91-105">Configuration 요소 (Format) Viewcontrolelement (Format) View Element (format) GroupBy 요소 (GroupBy)의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ec91-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ec91-106">구문</span><span class="sxs-lookup"><span data-stu-id="4ec91-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ec91-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4ec91-107">Attributes and Elements</span></span>

<span data-ttu-id="4ec91-108">다음 섹션에서는 `CustomControlName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ec91-109">특성</span><span class="sxs-lookup"><span data-stu-id="4ec91-109">Attributes</span></span>

<span data-ttu-id="4ec91-110">없음</span><span class="sxs-lookup"><span data-stu-id="4ec91-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ec91-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4ec91-111">Child Elements</span></span>

<span data-ttu-id="4ec91-112">없음</span><span class="sxs-lookup"><span data-stu-id="4ec91-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ec91-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4ec91-113">Parent Elements</span></span>

|<span data-ttu-id="4ec91-114">요소</span><span class="sxs-lookup"><span data-stu-id="4ec91-114">Element</span></span>|<span data-ttu-id="4ec91-115">설명</span><span class="sxs-lookup"><span data-stu-id="4ec91-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ec91-116">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ec91-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4ec91-117">Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ec91-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4ec91-118">Text Value</span></span>

<span data-ttu-id="4ec91-119">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ec91-120">설명</span><span class="sxs-lookup"><span data-stu-id="4ec91-120">Remarks</span></span>

<span data-ttu-id="4ec91-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="4ec91-122">다음 요소는 이러한 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec91-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="4ec91-123">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ec91-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="4ec91-124">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4ec91-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="4ec91-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ec91-125">See Also</span></span>

[<span data-ttu-id="4ec91-126">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ec91-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4ec91-127">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ec91-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="4ec91-128">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4ec91-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4ec91-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4ec91-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
