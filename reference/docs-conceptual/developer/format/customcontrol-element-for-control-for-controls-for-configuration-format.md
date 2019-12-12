---
title: 구성 (형식)의 컨트롤에 대 한 CustomControl 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368972"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="95a3c-102">Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="95a3c-102">CustomControl Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="95a3c-103">컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-103">Defines a control.</span></span> <span data-ttu-id="95a3c-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="95a3c-105">구성 요소 (format) 컨트롤 요소 구성 (format)의 컨트롤 요소 구성 (format)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="95a3c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95a3c-106">구문</span><span class="sxs-lookup"><span data-stu-id="95a3c-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95a3c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="95a3c-107">Attributes and Elements</span></span>

<span data-ttu-id="95a3c-108">다음 섹션에서는 특성, 자식 요소 및 `CustomControl` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-108">The following sections describe the attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="95a3c-109">이 요소에는 자식 요소가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-109">This element must have at least one child element.</span></span> <span data-ttu-id="95a3c-110">지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="95a3c-111">특성</span><span class="sxs-lookup"><span data-stu-id="95a3c-111">Attributes</span></span>

<span data-ttu-id="95a3c-112">없음</span><span class="sxs-lookup"><span data-stu-id="95a3c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95a3c-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="95a3c-113">Child Elements</span></span>

|<span data-ttu-id="95a3c-114">요소</span><span class="sxs-lookup"><span data-stu-id="95a3c-114">Element</span></span>|<span data-ttu-id="95a3c-115">설명</span><span class="sxs-lookup"><span data-stu-id="95a3c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95a3c-116">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95a3c-116">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="95a3c-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-117">Required element.</span></span><br /><br /> <span data-ttu-id="95a3c-118">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-118">Provides the definitions of a control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95a3c-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="95a3c-119">Parent Elements</span></span>

|<span data-ttu-id="95a3c-120">요소</span><span class="sxs-lookup"><span data-stu-id="95a3c-120">Element</span></span>|<span data-ttu-id="95a3c-121">설명</span><span class="sxs-lookup"><span data-stu-id="95a3c-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95a3c-122">구성에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95a3c-122">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="95a3c-123">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="95a3c-123">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95a3c-124">설명</span><span class="sxs-lookup"><span data-stu-id="95a3c-124">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="95a3c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95a3c-125">See Also</span></span>

[<span data-ttu-id="95a3c-126">구성에 대 한 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95a3c-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="95a3c-127">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95a3c-127">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="95a3c-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="95a3c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
