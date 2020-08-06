---
title: EnumerableExpansions 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2b536b1ab9b34b0089d0a38d3c5dc7a937176443
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774017"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="07155-102">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="07155-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="07155-103">.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="07155-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="07155-104">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="07155-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07155-105">구문</span><span class="sxs-lookup"><span data-stu-id="07155-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07155-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="07155-106">Attributes and Elements</span></span>

<span data-ttu-id="07155-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EnumerableExpansions` .</span><span class="sxs-lookup"><span data-stu-id="07155-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="07155-108">사용할 수 있는 자식 요소 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07155-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="07155-109">특성</span><span class="sxs-lookup"><span data-stu-id="07155-109">Attributes</span></span>

<span data-ttu-id="07155-110">없음</span><span class="sxs-lookup"><span data-stu-id="07155-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07155-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="07155-111">Child Elements</span></span>

|<span data-ttu-id="07155-112">요소</span><span class="sxs-lookup"><span data-stu-id="07155-112">Element</span></span>|<span data-ttu-id="07155-113">설명</span><span class="sxs-lookup"><span data-stu-id="07155-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07155-114">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="07155-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="07155-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="07155-115">Optional element.</span></span><br /><br /> <span data-ttu-id="07155-116">뷰에 표시 될 때 확장 되는 특정 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="07155-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07155-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="07155-117">Parent Elements</span></span>

|<span data-ttu-id="07155-118">요소</span><span class="sxs-lookup"><span data-stu-id="07155-118">Element</span></span>|<span data-ttu-id="07155-119">설명</span><span class="sxs-lookup"><span data-stu-id="07155-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07155-120">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="07155-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="07155-121">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="07155-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07155-122">설명</span><span class="sxs-lookup"><span data-stu-id="07155-122">Remarks</span></span>

<span data-ttu-id="07155-123">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07155-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="07155-124">이 경우 컬렉션 개체는 **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="07155-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="07155-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07155-125">See Also</span></span>

[<span data-ttu-id="07155-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="07155-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
