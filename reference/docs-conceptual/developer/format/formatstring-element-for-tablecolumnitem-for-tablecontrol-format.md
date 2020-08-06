---
title: TableControl (형식)의 TableColumnItem에 대 한 FormatString 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781548"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="fa37f-102">TableControl의 TableColumnItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fa37f-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="fa37f-103">테이블의 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa37f-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="fa37f-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry Element (format) TableColumnItems element (format) TableColumnItem element (format) FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fa37f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa37f-105">구문</span><span class="sxs-lookup"><span data-stu-id="fa37f-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa37f-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fa37f-106">Attributes and Elements</span></span>

<span data-ttu-id="fa37f-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `FormatString` .</span><span class="sxs-lookup"><span data-stu-id="fa37f-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa37f-108">특성</span><span class="sxs-lookup"><span data-stu-id="fa37f-108">Attributes</span></span>

<span data-ttu-id="fa37f-109">없음</span><span class="sxs-lookup"><span data-stu-id="fa37f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa37f-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fa37f-110">Child Elements</span></span>

<span data-ttu-id="fa37f-111">없음</span><span class="sxs-lookup"><span data-stu-id="fa37f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fa37f-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fa37f-112">Parent Elements</span></span>

|<span data-ttu-id="fa37f-113">요소</span><span class="sxs-lookup"><span data-stu-id="fa37f-113">Element</span></span>|<span data-ttu-id="fa37f-114">설명</span><span class="sxs-lookup"><span data-stu-id="fa37f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa37f-115">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="fa37f-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="fa37f-116">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa37f-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fa37f-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="fa37f-117">Text Value</span></span>

<span data-ttu-id="fa37f-118">데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa37f-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="fa37f-119">예를 들어이 패턴을 사용 하 여 [System. Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0: HH}: {0: mm} 형식의 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa37f-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa37f-120">설명</span><span class="sxs-lookup"><span data-stu-id="fa37f-120">Remarks</span></span>

<span data-ttu-id="fa37f-121">형식 문자열은 테이블 뷰, 목록 뷰, 넓은 뷰 또는 사용자 지정 뷰를 만들 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa37f-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="fa37f-122">뷰에 표시 되는 값의 서식을 지정 하는 방법에 대 한 자세한 내용은 [표시 된 데이터 서식 지정](./formatting-displayed-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa37f-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="fa37f-123">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa37f-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fa37f-124">예제</span><span class="sxs-lookup"><span data-stu-id="fa37f-124">Example</span></span>

<span data-ttu-id="fa37f-125">다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .</span><span class="sxs-lookup"><span data-stu-id="fa37f-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="fa37f-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa37f-126">See Also</span></span>

[<span data-ttu-id="fa37f-127">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="fa37f-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fa37f-128">표시되는 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="fa37f-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="fa37f-129">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="fa37f-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="fa37f-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fa37f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
