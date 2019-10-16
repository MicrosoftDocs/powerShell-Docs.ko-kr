---
title: TableControl (형식)의 TableColumnItem에 대 한 FormatString 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363712"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="08223-102">TableControl의 TableColumnItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08223-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="08223-103">테이블의 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08223-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="08223-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) TableColumnItems Element (format) TableColumnItem 요소 (format) TableColumnItem에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="08223-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08223-105">구문</span><span class="sxs-lookup"><span data-stu-id="08223-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08223-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="08223-106">Attributes and Elements</span></span>

<span data-ttu-id="08223-107">다음 섹션에서는 `FormatString` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="08223-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08223-108">특성</span><span class="sxs-lookup"><span data-stu-id="08223-108">Attributes</span></span>

<span data-ttu-id="08223-109">없음</span><span class="sxs-lookup"><span data-stu-id="08223-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08223-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="08223-110">Child Elements</span></span>

<span data-ttu-id="08223-111">없음</span><span class="sxs-lookup"><span data-stu-id="08223-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08223-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="08223-112">Parent Elements</span></span>

|<span data-ttu-id="08223-113">요소</span><span class="sxs-lookup"><span data-stu-id="08223-113">Element</span></span>|<span data-ttu-id="08223-114">설명</span><span class="sxs-lookup"><span data-stu-id="08223-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08223-115">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="08223-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="08223-116">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08223-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08223-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="08223-117">Text Value</span></span>

<span data-ttu-id="08223-118">데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08223-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="08223-119">예를 들어이 패턴을 사용 하 여 [System. Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0: HH}: {0: mm} 형식의 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08223-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="08223-120">설명</span><span class="sxs-lookup"><span data-stu-id="08223-120">Remarks</span></span>

<span data-ttu-id="08223-121">형식 문자열은 테이블 뷰, 목록 뷰, 넓은 뷰 또는 사용자 지정 뷰를 만들 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08223-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="08223-122">뷰에 표시 되는 값의 서식을 지정 하는 방법에 대 한 자세한 내용은 [표시 된 데이터 서식 지정](./formatting-displayed-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08223-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="08223-123">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08223-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="08223-124">예제</span><span class="sxs-lookup"><span data-stu-id="08223-124">Example</span></span>

<span data-ttu-id="08223-125">다음 예에서는 `StartTime` 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="08223-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="08223-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08223-126">See Also</span></span>

[<span data-ttu-id="08223-127">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="08223-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="08223-128">표시 된 데이터 서식 지정</span><span class="sxs-lookup"><span data-stu-id="08223-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="08223-129">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="08223-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="08223-130">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="08223-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
