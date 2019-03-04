---
title: GroupBy (형식)에 대 한 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863269"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="44b99-102">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="44b99-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="44b99-103">해당 값이 변경 될 때마다 새 그룹을 시작 하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="44b99-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 GroupBy (형식)에 대 한 보기 (형식) PropertyName 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="44b99-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44b99-105">구문</span><span class="sxs-lookup"><span data-stu-id="44b99-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44b99-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="44b99-106">Attributes and Elements</span></span>

<span data-ttu-id="44b99-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44b99-108">특성</span><span class="sxs-lookup"><span data-stu-id="44b99-108">Attributes</span></span>

<span data-ttu-id="44b99-109">없음</span><span class="sxs-lookup"><span data-stu-id="44b99-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44b99-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="44b99-110">Child Elements</span></span>

<span data-ttu-id="44b99-111">없음</span><span class="sxs-lookup"><span data-stu-id="44b99-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="44b99-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="44b99-112">Parent Elements</span></span>

|<span data-ttu-id="44b99-113">요소</span><span class="sxs-lookup"><span data-stu-id="44b99-113">Element</span></span>|<span data-ttu-id="44b99-114">설명</span><span class="sxs-lookup"><span data-stu-id="44b99-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44b99-115">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="44b99-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="44b99-116">.NET 개체 그룹에 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="44b99-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="44b99-117">Text Value</span></span>

<span data-ttu-id="44b99-118">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="44b99-119">설명</span><span class="sxs-lookup"><span data-stu-id="44b99-119">Remarks</span></span>

<span data-ttu-id="44b99-120">Windows PowerShell이이 속성의 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="44b99-121">이 요소를 지정 하는 경우 지정할 수 없습니다는 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소를 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="44b99-122">예제</span><span class="sxs-lookup"><span data-stu-id="44b99-122">Example</span></span>

<span data-ttu-id="44b99-123">다음 예제에서는 속성의 값 변경 시 새 그룹을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="44b99-124">이 요소를 포함 하는 전체 서식 파일의 예제를 보려면 [넓은 보기 (GroupBy)](./wide-view-groupby.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="44b99-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44b99-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44b99-125">See Also</span></span>

[<span data-ttu-id="44b99-126">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="44b99-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="44b99-127">GroupBy (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="44b99-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="44b99-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="44b99-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
