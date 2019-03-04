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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860309"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="a2e1f-102">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a2e1f-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="a2e1f-103">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="a2e1f-104">이 요소는 테이블, 목록, 와이드 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="a2e1f-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 (형식) 보기 CustomControlName 요소의 GroupBy (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="a2e1f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a2e1f-106">구문</span><span class="sxs-lookup"><span data-stu-id="a2e1f-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2e1f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-107">Attributes and Elements</span></span>

<span data-ttu-id="a2e1f-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomControlName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2e1f-109">특성</span><span class="sxs-lookup"><span data-stu-id="a2e1f-109">Attributes</span></span>

<span data-ttu-id="a2e1f-110">없음</span><span class="sxs-lookup"><span data-stu-id="a2e1f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2e1f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-111">Child Elements</span></span>

<span data-ttu-id="a2e1f-112">없음</span><span class="sxs-lookup"><span data-stu-id="a2e1f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2e1f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-113">Parent Elements</span></span>

|<span data-ttu-id="a2e1f-114">요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-114">Element</span></span>|<span data-ttu-id="a2e1f-115">설명</span><span class="sxs-lookup"><span data-stu-id="a2e1f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2e1f-116">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a2e1f-117">Windows PowerShell에서 개체의 새 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a2e1f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="a2e1f-118">Text Value</span></span>

<span data-ttu-id="a2e1f-119">새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2e1f-120">설명</span><span class="sxs-lookup"><span data-stu-id="a2e1f-120">Remarks</span></span>

<span data-ttu-id="a2e1f-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있습니다 하 고 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a2e1f-122">다음 요소에는 이러한 사용자 지정 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e1f-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="a2e1f-123">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a2e1f-124">뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a2e1f-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2e1f-125">See Also</span></span>

[<span data-ttu-id="a2e1f-126">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a2e1f-127">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a2e1f-128">뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="a2e1f-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a2e1f-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="a2e1f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
