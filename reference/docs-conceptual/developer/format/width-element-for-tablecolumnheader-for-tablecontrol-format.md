---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnHeader에 대한 Width 요소(형식)
description: TableControl의 TableColumnHeader에 대한 Width 요소(형식)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658256"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="cba47-103">TableControl의 TableColumnHeader에 대한 Width 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cba47-103">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="cba47-104">열의 너비 (문자)를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba47-104">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="cba47-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableColumnHeader Element의 TableHeaders 요소에 대 한 TableControl (형식) 요소 TableHeaders for TableColumnHeader for TableControl (형식)에 대 한의 Width 요소</span><span class="sxs-lookup"><span data-stu-id="cba47-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cba47-106">구문</span><span class="sxs-lookup"><span data-stu-id="cba47-106">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cba47-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cba47-107">Attributes and Elements</span></span>

<span data-ttu-id="cba47-108">다음 섹션에서는 `Width` 열 헤더를 정의할 때 사용 되는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba47-108">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="cba47-109">특성</span><span class="sxs-lookup"><span data-stu-id="cba47-109">Attributes</span></span>

<span data-ttu-id="cba47-110">없음</span><span class="sxs-lookup"><span data-stu-id="cba47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cba47-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cba47-111">Child Elements</span></span>

<span data-ttu-id="cba47-112">없음</span><span class="sxs-lookup"><span data-stu-id="cba47-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cba47-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cba47-113">Parent Elements</span></span>

|<span data-ttu-id="cba47-114">요소</span><span class="sxs-lookup"><span data-stu-id="cba47-114">Element</span></span>|<span data-ttu-id="cba47-115">설명</span><span class="sxs-lookup"><span data-stu-id="cba47-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cba47-116">TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소</span><span class="sxs-lookup"><span data-stu-id="cba47-116">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="cba47-117">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba47-117">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cba47-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="cba47-118">Text Value</span></span>

<span data-ttu-id="cba47-119">가능 하면 표시 된 속성 값의 길이 보다 큰 너비 (문자)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cba47-119">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="cba47-120">설명</span><span class="sxs-lookup"><span data-stu-id="cba47-120">Remarks</span></span>

<span data-ttu-id="cba47-121">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cba47-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cba47-122">예제</span><span class="sxs-lookup"><span data-stu-id="cba47-122">Example</span></span>

<span data-ttu-id="cba47-123">다음 예제에서는 `TableColumnHeader` 너비가 16 자인 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cba47-123">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="cba47-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cba47-124">See Also</span></span>

[<span data-ttu-id="cba47-125">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="cba47-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cba47-126">TableControl의 TableHeader에 대 한 TableColumnHeader 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cba47-126">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="cba47-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cba47-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
