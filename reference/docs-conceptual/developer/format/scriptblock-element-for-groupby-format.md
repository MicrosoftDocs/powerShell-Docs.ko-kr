---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy에 대한 ScriptBlock 요소(형식)
description: GroupBy에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665239"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="e3f8c-103">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e3f8c-103">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="e3f8c-104">값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f8c-104">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="e3f8c-105">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (Format) GroupBy 요소에 대 한 groupby 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e3f8c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3f8c-106">구문</span><span class="sxs-lookup"><span data-stu-id="e3f8c-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3f8c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e3f8c-107">Attributes and Elements</span></span>

<span data-ttu-id="e3f8c-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="e3f8c-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3f8c-109">특성</span><span class="sxs-lookup"><span data-stu-id="e3f8c-109">Attributes</span></span>

<span data-ttu-id="e3f8c-110">없음</span><span class="sxs-lookup"><span data-stu-id="e3f8c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3f8c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e3f8c-111">Child Elements</span></span>

<span data-ttu-id="e3f8c-112">없음</span><span class="sxs-lookup"><span data-stu-id="e3f8c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3f8c-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e3f8c-113">Parent Elements</span></span>

|<span data-ttu-id="e3f8c-114">요소</span><span class="sxs-lookup"><span data-stu-id="e3f8c-114">Element</span></span>|<span data-ttu-id="e3f8c-115">설명</span><span class="sxs-lookup"><span data-stu-id="e3f8c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3f8c-116">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e3f8c-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e3f8c-117">.NET 개체 그룹이 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f8c-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3f8c-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e3f8c-118">Text Value</span></span>

<span data-ttu-id="e3f8c-119">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f8c-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3f8c-120">설명</span><span class="sxs-lookup"><span data-stu-id="e3f8c-120">Remarks</span></span>

<span data-ttu-id="e3f8c-121">PowerShell은이 스크립트의 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f8c-121">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="e3f8c-122">이 요소를 지정 하면 새 그룹을 시작 하는 [PropertyName](propertyname-element-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f8c-122">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3f8c-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3f8c-123">See Also</span></span>

[<span data-ttu-id="e3f8c-124">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e3f8c-124">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="e3f8c-125">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e3f8c-125">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="e3f8c-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e3f8c-126">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
