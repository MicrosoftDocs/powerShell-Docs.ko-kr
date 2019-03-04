---
title: 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 CustomControl 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857669"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="08a09-102">Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08a09-102">CustomControl Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="08a09-103">컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-103">Defines a control.</span></span> <span data-ttu-id="08a09-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="08a09-105">구성 (형식)에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08a09-106">구문</span><span class="sxs-lookup"><span data-stu-id="08a09-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08a09-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-107">Attributes and Elements</span></span>

<span data-ttu-id="08a09-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControl` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-108">The following sections describe the attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="08a09-109">이 요소에 자식 요소가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-109">This element must have at least one child element.</span></span> <span data-ttu-id="08a09-110">지정할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="08a09-111">특성</span><span class="sxs-lookup"><span data-stu-id="08a09-111">Attributes</span></span>

<span data-ttu-id="08a09-112">없음</span><span class="sxs-lookup"><span data-stu-id="08a09-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08a09-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-113">Child Elements</span></span>

|<span data-ttu-id="08a09-114">요소</span><span class="sxs-lookup"><span data-stu-id="08a09-114">Element</span></span>|<span data-ttu-id="08a09-115">설명</span><span class="sxs-lookup"><span data-stu-id="08a09-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a09-116">구성 (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-116">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="08a09-117">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-117">Required element.</span></span><br /><br /> <span data-ttu-id="08a09-118">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-118">Provides the definitions of a control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08a09-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-119">Parent Elements</span></span>

|<span data-ttu-id="08a09-120">요소</span><span class="sxs-lookup"><span data-stu-id="08a09-120">Element</span></span>|<span data-ttu-id="08a09-121">설명</span><span class="sxs-lookup"><span data-stu-id="08a09-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a09-122">구성 (형식)에 대 한 컨트롤에 대 한 control 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-122">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="08a09-123">컨트롤을 참조 하는 데 사용 되는 이름과 형식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08a09-123">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08a09-124">설명</span><span class="sxs-lookup"><span data-stu-id="08a09-124">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="08a09-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08a09-125">See Also</span></span>

[<span data-ttu-id="08a09-126">구성 (형식)에 대 한 컨트롤에 대 한 control 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="08a09-127">구성 (형식)에 대 한 CustomControl CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="08a09-127">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="08a09-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="08a09-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
