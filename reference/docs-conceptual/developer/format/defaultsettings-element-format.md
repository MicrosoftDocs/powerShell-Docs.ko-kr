---
ms.date: 09/13/2016
ms.topic: reference
title: DefaultSettings 요소(형식)
description: DefaultSettings 요소(형식)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666725"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="153b4-103">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-103">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="153b4-104">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-104">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="153b4-105">일반 설정에는 오류 표시, 테이블에 텍스트 줄 바꿈, 컬렉션이 확장 되는 방법 정의 등이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-105">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="153b4-106">Configuration 요소 (Format) DefaultSettings 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="153b4-106">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="153b4-107">구문</span><span class="sxs-lookup"><span data-stu-id="153b4-107">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="153b4-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="153b4-108">Attributes and Elements</span></span>

<span data-ttu-id="153b4-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `DefaultSettings` .</span><span class="sxs-lookup"><span data-stu-id="153b4-109">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="153b4-110">특성</span><span class="sxs-lookup"><span data-stu-id="153b4-110">Attributes</span></span>

<span data-ttu-id="153b4-111">없음</span><span class="sxs-lookup"><span data-stu-id="153b4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="153b4-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="153b4-112">Child Elements</span></span>

|<span data-ttu-id="153b4-113">요소</span><span class="sxs-lookup"><span data-stu-id="153b4-113">Element</span></span>|<span data-ttu-id="153b4-114">설명</span><span class="sxs-lookup"><span data-stu-id="153b4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="153b4-115">DisplayError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-115">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="153b4-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="153b4-117">데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-117">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="153b4-118">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-118">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="153b4-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="153b4-120">.NET 개체가 뷰에 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-120">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="153b4-121">PropertyCountForTable (형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-121">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="153b4-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="153b4-123">개체가 테이블 뷰에 개체를 표시 하는 데 필요한 최소 속성 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-123">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="153b4-124">ShowError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-124">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="153b4-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="153b4-126">데이터 조각을 표시 하는 동안 오류가 발생 하면 전체 오류 레코드가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-126">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="153b4-127">WrapTables 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-127">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="153b4-128">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-128">Optional element.</span></span><br /><br /> <span data-ttu-id="153b4-129">열의 너비에 맞지 않는 경우 테이블의 데이터를 다음 줄로 이동 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-129">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="153b4-130">부모 요소</span><span class="sxs-lookup"><span data-stu-id="153b4-130">Parent Elements</span></span>

|<span data-ttu-id="153b4-131">요소</span><span class="sxs-lookup"><span data-stu-id="153b4-131">Element</span></span>|<span data-ttu-id="153b4-132">설명</span><span class="sxs-lookup"><span data-stu-id="153b4-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="153b4-133">구성 요소</span><span class="sxs-lookup"><span data-stu-id="153b4-133">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="153b4-134">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="153b4-134">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="153b4-135">설명</span><span class="sxs-lookup"><span data-stu-id="153b4-135">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="153b4-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="153b4-136">See Also</span></span>

[<span data-ttu-id="153b4-137">구성 요소</span><span class="sxs-lookup"><span data-stu-id="153b4-137">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="153b4-138">DisplayError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-138">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="153b4-139">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-139">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="153b4-140">PropertyCountForTable (형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-140">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="153b4-141">ShowError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-141">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="153b4-142">WrapTables 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="153b4-142">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="153b4-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="153b4-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
