---
title: DefaultSettings 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363872"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="c4496-102">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c4496-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="c4496-103">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="c4496-104">일반 설정에는 오류 표시, 테이블에 텍스트 줄 바꿈, 컬렉션이 확장 되는 방법 정의 등이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="c4496-105">Configuration 요소 (Format) DefaultSettings 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4496-106">구문</span><span class="sxs-lookup"><span data-stu-id="c4496-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4496-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c4496-107">Attributes and Elements</span></span>

<span data-ttu-id="c4496-108">다음 섹션에서는 `DefaultSettings` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4496-109">특성</span><span class="sxs-lookup"><span data-stu-id="c4496-109">Attributes</span></span>

<span data-ttu-id="c4496-110">없음</span><span class="sxs-lookup"><span data-stu-id="c4496-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4496-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c4496-111">Child Elements</span></span>

|<span data-ttu-id="c4496-112">요소</span><span class="sxs-lookup"><span data-stu-id="c4496-112">Element</span></span>|<span data-ttu-id="c4496-113">설명</span><span class="sxs-lookup"><span data-stu-id="c4496-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4496-114">DisplayError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="c4496-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c4496-116">데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="c4496-117">EnumerableExpansions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4496-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="c4496-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c4496-119">.NET 개체가 뷰에 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="c4496-120">PropertyCountForTable (형식)</span><span class="sxs-lookup"><span data-stu-id="c4496-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="c4496-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c4496-122">개체가 테이블 뷰에 개체를 표시 하는 데 필요한 최소 속성 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="c4496-123">ShowError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="c4496-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c4496-125">데이터 조각을 표시 하는 동안 오류가 발생 하면 전체 오류 레코드가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="c4496-126">WrapTables 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="c4496-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-127">Optional element.</span></span><br /><br /> <span data-ttu-id="c4496-128">열의 너비에 맞지 않는 경우 테이블의 데이터를 다음 줄로 이동 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4496-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c4496-129">Parent Elements</span></span>

|<span data-ttu-id="c4496-130">요소</span><span class="sxs-lookup"><span data-stu-id="c4496-130">Element</span></span>|<span data-ttu-id="c4496-131">설명</span><span class="sxs-lookup"><span data-stu-id="c4496-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4496-132">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c4496-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="c4496-133">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4496-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4496-134">설명</span><span class="sxs-lookup"><span data-stu-id="c4496-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c4496-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4496-135">See Also</span></span>

[<span data-ttu-id="c4496-136">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c4496-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="c4496-137">DisplayError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="c4496-138">EnumerableExpansions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4496-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="c4496-139">PropertyCountForTable (형식)</span><span class="sxs-lookup"><span data-stu-id="c4496-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="c4496-140">ShowError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="c4496-141">WrapTables 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c4496-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="c4496-142">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c4496-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
