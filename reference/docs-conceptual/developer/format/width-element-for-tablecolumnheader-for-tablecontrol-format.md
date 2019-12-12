---
title: TableControl (형식)의 TableColumnHeader에 대 한 Width 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367872"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="f2126-102">TableControl의 TableColumnHeader에 대한 Width 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f2126-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="f2126-103">열의 너비 (문자)를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2126-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="f2126-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableColumnHeader Element의 TableHeaders 요소에 대 한 TableControl (Format) Width 요소의 TableHeaders TableControl에 대 한 TableColumnHeader (형식)</span><span class="sxs-lookup"><span data-stu-id="f2126-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2126-105">구문</span><span class="sxs-lookup"><span data-stu-id="f2126-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2126-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f2126-106">Attributes and Elements</span></span>

<span data-ttu-id="f2126-107">다음 섹션에서는 열 머리글을 정의할 때 사용 되는 `Width` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2126-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2126-108">특성</span><span class="sxs-lookup"><span data-stu-id="f2126-108">Attributes</span></span>

<span data-ttu-id="f2126-109">없음</span><span class="sxs-lookup"><span data-stu-id="f2126-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2126-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f2126-110">Child Elements</span></span>

<span data-ttu-id="f2126-111">없음</span><span class="sxs-lookup"><span data-stu-id="f2126-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2126-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f2126-112">Parent Elements</span></span>

|<span data-ttu-id="f2126-113">요소</span><span class="sxs-lookup"><span data-stu-id="f2126-113">Element</span></span>|<span data-ttu-id="f2126-114">설명</span><span class="sxs-lookup"><span data-stu-id="f2126-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2126-115">TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소</span><span class="sxs-lookup"><span data-stu-id="f2126-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="f2126-116">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2126-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2126-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="f2126-117">Text Value</span></span>

<span data-ttu-id="f2126-118">가능 하면 표시 된 속성 값의 길이 보다 큰 너비 (문자)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2126-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2126-119">설명</span><span class="sxs-lookup"><span data-stu-id="f2126-119">Remarks</span></span>

<span data-ttu-id="f2126-120">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2126-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2126-121">예제</span><span class="sxs-lookup"><span data-stu-id="f2126-121">Example</span></span>

<span data-ttu-id="f2126-122">다음 예제에서는 너비가 16 자인 `TableColumnHeader` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2126-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="f2126-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2126-123">See Also</span></span>

[<span data-ttu-id="f2126-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="f2126-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f2126-125">TableControl의 TableHeader에 대 한 TableColumnHeader 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f2126-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="f2126-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f2126-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
