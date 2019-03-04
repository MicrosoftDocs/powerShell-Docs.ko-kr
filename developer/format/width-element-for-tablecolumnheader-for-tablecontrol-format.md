---
title: TableControl (형식)에 대 한 TableColumnHeader 너비 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853109"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="dd3ff-102">TableControl의 TableColumnHeader에 대한 Width 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd3ff-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="dd3ff-103">너비 (문자 단위) 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ff-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="dd3ff-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableHeaders 요소에 대 한 너비 요소 TableControl (형식)에 대 한 TableColumnHeader 요소 TableHeaders TableControl (형식)에 대 한 TableControl (형식)에 대 한 TableColumnHeader</span><span class="sxs-lookup"><span data-stu-id="dd3ff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd3ff-105">구문</span><span class="sxs-lookup"><span data-stu-id="dd3ff-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd3ff-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="dd3ff-106">Attributes and Elements</span></span>

<span data-ttu-id="dd3ff-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Width` 열 헤더를 정의할 때 사용 되는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ff-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd3ff-108">특성</span><span class="sxs-lookup"><span data-stu-id="dd3ff-108">Attributes</span></span>

<span data-ttu-id="dd3ff-109">없음</span><span class="sxs-lookup"><span data-stu-id="dd3ff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd3ff-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="dd3ff-110">Child Elements</span></span>

<span data-ttu-id="dd3ff-111">없음</span><span class="sxs-lookup"><span data-stu-id="dd3ff-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd3ff-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="dd3ff-112">Parent Elements</span></span>

|<span data-ttu-id="dd3ff-113">요소</span><span class="sxs-lookup"><span data-stu-id="dd3ff-113">Element</span></span>|<span data-ttu-id="dd3ff-114">설명</span><span class="sxs-lookup"><span data-stu-id="dd3ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd3ff-115">TbleControl (형식)에 대 한 TableHeaders TableColumnHeader 요소</span><span class="sxs-lookup"><span data-stu-id="dd3ff-115">TableColumnHeader Element for TableHeaders for TbleControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="dd3ff-116">레이블, 너비 및 맞춤의 데이터 테이블의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ff-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd3ff-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="dd3ff-117">Text Value</span></span>

<span data-ttu-id="dd3ff-118">모든 가능한에 때 표시 된 속성 값의 길이 보다 큰 문자에서 너비를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ff-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd3ff-119">설명</span><span class="sxs-lookup"><span data-stu-id="dd3ff-119">Remarks</span></span>

<span data-ttu-id="dd3ff-120">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ff-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dd3ff-121">예제</span><span class="sxs-lookup"><span data-stu-id="dd3ff-121">Example</span></span>

<span data-ttu-id="dd3ff-122">다음 예제와 `TableColumnHeader` 너비가 16 자 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ff-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="dd3ff-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd3ff-123">See Also</span></span>

[<span data-ttu-id="dd3ff-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="dd3ff-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="dd3ff-125">TableControl (형식)에 대 한 TableHeader TableColumnHeader 요소</span><span class="sxs-lookup"><span data-stu-id="dd3ff-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="dd3ff-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="dd3ff-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
