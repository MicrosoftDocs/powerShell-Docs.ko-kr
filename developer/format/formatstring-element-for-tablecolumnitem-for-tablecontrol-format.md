---
title: TableControl (형식)에 대 한 TableColumnItem FormatString 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854329"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="e926b-102">TableControl의 TableColumnItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e926b-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="e926b-103">테이블의 속성이 나 스크립트 값 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="e926b-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) TableColumnItems 요소 (형식) TableColumnItem 요소 (형식) FormatString 요소 TableColumnItem (형식)</span><span class="sxs-lookup"><span data-stu-id="e926b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e926b-105">구문</span><span class="sxs-lookup"><span data-stu-id="e926b-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e926b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e926b-106">Attributes and Elements</span></span>

<span data-ttu-id="e926b-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `FormatString` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e926b-108">특성</span><span class="sxs-lookup"><span data-stu-id="e926b-108">Attributes</span></span>

<span data-ttu-id="e926b-109">없음</span><span class="sxs-lookup"><span data-stu-id="e926b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e926b-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e926b-110">Child Elements</span></span>

<span data-ttu-id="e926b-111">없음</span><span class="sxs-lookup"><span data-stu-id="e926b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e926b-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e926b-112">Parent Elements</span></span>

|<span data-ttu-id="e926b-113">요소</span><span class="sxs-lookup"><span data-stu-id="e926b-113">Element</span></span>|<span data-ttu-id="e926b-114">설명</span><span class="sxs-lookup"><span data-stu-id="e926b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e926b-115">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e926b-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e926b-116">속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e926b-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e926b-117">Text Value</span></span>

<span data-ttu-id="e926b-118">데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="e926b-119">형식의 모든 속성의 값 형식을 지정 하려면이 패턴을 사용할 수 있습니다 예를 들어 [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {{0:mm}&fmt=csv}.</span><span class="sxs-lookup"><span data-stu-id="e926b-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="e926b-120">설명</span><span class="sxs-lookup"><span data-stu-id="e926b-120">Remarks</span></span>

<span data-ttu-id="e926b-121">테이블 뷰, 목록 뷰, 와이드 뷰 또는 사용자 지정 보기를 만들 때 형식 문자열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="e926b-122">보기에 표시 된 값 형식에 대 한 자세한 내용은 참조 하세요. [표시 된 데이터 서식 지정](./formatting-displayed-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="e926b-123">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e926b-124">예제</span><span class="sxs-lookup"><span data-stu-id="e926b-124">Example</span></span>

<span data-ttu-id="e926b-125">다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e926b-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="e926b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e926b-126">See Also</span></span>

[<span data-ttu-id="e926b-127">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="e926b-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e926b-128">표시 되는 데이터 서식 지정</span><span class="sxs-lookup"><span data-stu-id="e926b-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="e926b-129">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e926b-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="e926b-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e926b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
