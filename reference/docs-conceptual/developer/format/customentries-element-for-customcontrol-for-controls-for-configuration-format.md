---
title: 구성 (형식)에 대 한 CustomControl의 CustomEntries 요소 Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368822"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="0bd70-102">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0bd70-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0bd70-103">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="0bd70-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0bd70-105">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 형식과</span><span class="sxs-lookup"><span data-stu-id="0bd70-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bd70-106">구문</span><span class="sxs-lookup"><span data-stu-id="0bd70-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0bd70-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-107">Attributes and Elements</span></span>

<span data-ttu-id="0bd70-108">다음 섹션에서는 `CustomEntries` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="0bd70-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bd70-110">특성</span><span class="sxs-lookup"><span data-stu-id="0bd70-110">Attributes</span></span>

<span data-ttu-id="0bd70-111">없음</span><span class="sxs-lookup"><span data-stu-id="0bd70-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bd70-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-112">Child Elements</span></span>

|<span data-ttu-id="0bd70-113">요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-113">Element</span></span>|<span data-ttu-id="0bd70-114">설명</span><span class="sxs-lookup"><span data-stu-id="0bd70-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bd70-115">구성에 대 한 CustomControl의 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0bd70-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0bd70-116">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0bd70-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-117">Parent Elements</span></span>

|<span data-ttu-id="0bd70-118">요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-118">Element</span></span>|<span data-ttu-id="0bd70-119">설명</span><span class="sxs-lookup"><span data-stu-id="0bd70-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bd70-120">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="0bd70-121">공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0bd70-122">설명</span><span class="sxs-lookup"><span data-stu-id="0bd70-122">Remarks</span></span>

<span data-ttu-id="0bd70-123">대부분의 경우 컨트롤에는 단일 `CustomEntry` 요소에 정의 된 정의가 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="0bd70-124">그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="0bd70-125">이러한 경우 각 개체 또는 개체 집합에 대 한 `CustomEntry` 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bd70-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bd70-126">See Also</span></span>

[<span data-ttu-id="0bd70-127">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="0bd70-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bd70-128">구성에 대 한 CustomControl의 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0bd70-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bd70-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0bd70-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
