---
title: DefaultSettings 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059068"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="05741-102">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05741-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="05741-103">서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="05741-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="05741-104">일반적인 설정의 컬렉션 확장 되는 방법을 정의 하는 테이블 및 기타 자동 줄 바꿈 오류 표시 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05741-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="05741-105">구성 요소 (형식) DefaultSettings 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05741-106">구문</span><span class="sxs-lookup"><span data-stu-id="05741-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05741-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="05741-107">Attributes and Elements</span></span>

<span data-ttu-id="05741-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `DefaultSettings` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05741-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05741-109">특성</span><span class="sxs-lookup"><span data-stu-id="05741-109">Attributes</span></span>

<span data-ttu-id="05741-110">없음</span><span class="sxs-lookup"><span data-stu-id="05741-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05741-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="05741-111">Child Elements</span></span>

|<span data-ttu-id="05741-112">요소</span><span class="sxs-lookup"><span data-stu-id="05741-112">Element</span></span>|<span data-ttu-id="05741-113">설명</span><span class="sxs-lookup"><span data-stu-id="05741-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05741-114">DisplayError 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="05741-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05741-115">Optional element.</span></span><br /><br /> <span data-ttu-id="05741-116">일부 데이터를 표시 하는 동안 오류가 발생 하면 #ERR 문자열 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05741-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="05741-117">EnumerableExpansions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="05741-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05741-118">Optional element.</span></span><br /><br /> <span data-ttu-id="05741-119">.NET 개체 뷰의 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="05741-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="05741-120">PropertyCountForTable (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="05741-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05741-121">Optional element.</span></span><br /><br /> <span data-ttu-id="05741-122">개체 표 보기에서 개체를 표시 해야 하는 속성의 최소 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05741-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="05741-123">ShowError 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="05741-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05741-124">Optional element.</span></span><br /><br /> <span data-ttu-id="05741-125">일부 데이터를 표시 하는 동안 오류가 발생 하면 전체 오류 레코드 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05741-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="05741-126">WrapTables 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="05741-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05741-127">Optional element.</span></span><br /><br /> <span data-ttu-id="05741-128">테이블의 데이터 다음 줄으로 이동 되 면 열의 너비에 들어가지 않습니다 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05741-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="05741-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="05741-129">Parent Elements</span></span>

|<span data-ttu-id="05741-130">요소</span><span class="sxs-lookup"><span data-stu-id="05741-130">Element</span></span>|<span data-ttu-id="05741-131">설명</span><span class="sxs-lookup"><span data-stu-id="05741-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05741-132">구성 요소</span><span class="sxs-lookup"><span data-stu-id="05741-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="05741-133">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05741-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="05741-134">설명</span><span class="sxs-lookup"><span data-stu-id="05741-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="05741-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05741-135">See Also</span></span>

[<span data-ttu-id="05741-136">구성 요소</span><span class="sxs-lookup"><span data-stu-id="05741-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="05741-137">DisplayError 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="05741-138">EnumerableExpansions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="05741-139">PropertyCountForTable (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="05741-140">ShowError 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="05741-141">WrapTables 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05741-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="05741-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="05741-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
