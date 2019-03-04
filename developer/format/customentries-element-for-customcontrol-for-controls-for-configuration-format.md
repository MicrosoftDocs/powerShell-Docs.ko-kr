---
title: 구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856309"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="2a211-102">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2a211-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2a211-103">공용 컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="2a211-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2a211-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="2a211-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a211-106">구문</span><span class="sxs-lookup"><span data-stu-id="2a211-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a211-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-107">Attributes and Elements</span></span>

<span data-ttu-id="2a211-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomEntries` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="2a211-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a211-110">특성</span><span class="sxs-lookup"><span data-stu-id="2a211-110">Attributes</span></span>

<span data-ttu-id="2a211-111">없음</span><span class="sxs-lookup"><span data-stu-id="2a211-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a211-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-112">Child Elements</span></span>

|<span data-ttu-id="2a211-113">요소</span><span class="sxs-lookup"><span data-stu-id="2a211-113">Element</span></span>|<span data-ttu-id="2a211-114">설명</span><span class="sxs-lookup"><span data-stu-id="2a211-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a211-115">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="2a211-116">공용 컨트롤의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2a211-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-117">Parent Elements</span></span>

|<span data-ttu-id="2a211-118">요소</span><span class="sxs-lookup"><span data-stu-id="2a211-118">Element</span></span>|<span data-ttu-id="2a211-119">설명</span><span class="sxs-lookup"><span data-stu-id="2a211-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a211-120">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="2a211-121">공용 컨트롤을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2a211-122">설명</span><span class="sxs-lookup"><span data-stu-id="2a211-122">Remarks</span></span>

<span data-ttu-id="2a211-123">대부분의 경우 컨트롤에 단일에 정의 되어 있는 하나만 정의 `CustomEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="2a211-124">그러나는 다른.NET 개체를 표시 하려면 동일한 컨트롤을 사용 하려는 경우 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="2a211-125">이러한 경우에 정의할 수 있습니다는 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2a211-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a211-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a211-126">See Also</span></span>

[<span data-ttu-id="2a211-127">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2a211-128">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="2a211-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="2a211-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="2a211-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
