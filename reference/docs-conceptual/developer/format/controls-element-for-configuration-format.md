---
title: 구성 요소 (형식)에 대 한 Controls 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783792"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="b56a2-102">Configuration에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b56a2-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="b56a2-103">서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b56a2-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="b56a2-104">구성 요소 (형식) 컨트롤 구성 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b56a2-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b56a2-105">구문</span><span class="sxs-lookup"><span data-stu-id="b56a2-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b56a2-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b56a2-106">Attributes and Elements</span></span>

<span data-ttu-id="b56a2-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Controls` .</span><span class="sxs-lookup"><span data-stu-id="b56a2-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b56a2-108">특성</span><span class="sxs-lookup"><span data-stu-id="b56a2-108">Attributes</span></span>

<span data-ttu-id="b56a2-109">없음</span><span class="sxs-lookup"><span data-stu-id="b56a2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b56a2-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b56a2-110">Child Elements</span></span>

|<span data-ttu-id="b56a2-111">요소</span><span class="sxs-lookup"><span data-stu-id="b56a2-111">Element</span></span>|<span data-ttu-id="b56a2-112">설명</span><span class="sxs-lookup"><span data-stu-id="b56a2-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b56a2-113">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b56a2-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="b56a2-114">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b56a2-114">Required element.</span></span><br /><br /> <span data-ttu-id="b56a2-115">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b56a2-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b56a2-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b56a2-116">Parent Elements</span></span>

|<span data-ttu-id="b56a2-117">요소</span><span class="sxs-lookup"><span data-stu-id="b56a2-117">Element</span></span>|<span data-ttu-id="b56a2-118">설명</span><span class="sxs-lookup"><span data-stu-id="b56a2-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b56a2-119">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b56a2-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="b56a2-120">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b56a2-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b56a2-121">설명</span><span class="sxs-lookup"><span data-stu-id="b56a2-121">Remarks</span></span>

<span data-ttu-id="b56a2-122">원하는 수의 공용 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b56a2-122">You can create any number of common controls.</span></span> <span data-ttu-id="b56a2-123">각 컨트롤에 대해 컨트롤을 참조 하는 데 사용 되는 이름과 컨트롤의 구성 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b56a2-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="b56a2-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b56a2-124">See Also</span></span>

[<span data-ttu-id="b56a2-125">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b56a2-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="b56a2-126">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b56a2-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="b56a2-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b56a2-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
