---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnItem에 대한 FormatString 요소(형식)
description: TableControl의 TableColumnItem에 대한 FormatString 요소(형식)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667898"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="a461f-103">TableControl의 TableColumnItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a461f-103">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="a461f-104">테이블의 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a461f-104">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="a461f-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry Element (format) TableColumnItems element (format) TableColumnItem element (format) FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a461f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a461f-106">구문</span><span class="sxs-lookup"><span data-stu-id="a461f-106">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a461f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a461f-107">Attributes and Elements</span></span>

<span data-ttu-id="a461f-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `FormatString` .</span><span class="sxs-lookup"><span data-stu-id="a461f-108">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a461f-109">특성</span><span class="sxs-lookup"><span data-stu-id="a461f-109">Attributes</span></span>

<span data-ttu-id="a461f-110">없음</span><span class="sxs-lookup"><span data-stu-id="a461f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a461f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a461f-111">Child Elements</span></span>

<span data-ttu-id="a461f-112">없음</span><span class="sxs-lookup"><span data-stu-id="a461f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a461f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a461f-113">Parent Elements</span></span>

|<span data-ttu-id="a461f-114">요소</span><span class="sxs-lookup"><span data-stu-id="a461f-114">Element</span></span>|<span data-ttu-id="a461f-115">설명</span><span class="sxs-lookup"><span data-stu-id="a461f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a461f-116">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a461f-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a461f-117">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a461f-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a461f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="a461f-118">Text Value</span></span>

<span data-ttu-id="a461f-119">데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a461f-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="a461f-120">예를 들어이 패턴을 사용 하 여 [System. Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0: HH}: {0: mm} 형식의 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a461f-120">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="a461f-121">설명</span><span class="sxs-lookup"><span data-stu-id="a461f-121">Remarks</span></span>

<span data-ttu-id="a461f-122">형식 문자열은 테이블 뷰, 목록 뷰, 넓은 뷰 또는 사용자 지정 뷰를 만들 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a461f-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="a461f-123">뷰에 표시 되는 값의 서식을 지정 하는 방법에 대 한 자세한 내용은 [표시 된 데이터 서식 지정](./formatting-displayed-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a461f-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="a461f-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a461f-124">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a461f-125">예제</span><span class="sxs-lookup"><span data-stu-id="a461f-125">Example</span></span>

<span data-ttu-id="a461f-126">다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .</span><span class="sxs-lookup"><span data-stu-id="a461f-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="a461f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a461f-127">See Also</span></span>

[<span data-ttu-id="a461f-128">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="a461f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a461f-129">표시되는 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="a461f-129">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="a461f-130">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a461f-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="a461f-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a461f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
