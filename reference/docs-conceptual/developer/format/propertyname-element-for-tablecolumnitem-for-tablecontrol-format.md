---
title: TableControl (형식)의 TableColumnItem에 대 한 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bf267eeb83aef59abea2d945af12e849252309c8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772980"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="9d497-102">TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9d497-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="9d497-103">행의 열에 값이 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d497-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="9d497-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry element (format) TableColumnItems element (format) TableColumnItem element (format) PropertyName Element for TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="9d497-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d497-105">구문</span><span class="sxs-lookup"><span data-stu-id="9d497-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d497-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9d497-106">Attributes and Elements</span></span>

<span data-ttu-id="9d497-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="9d497-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d497-108">특성</span><span class="sxs-lookup"><span data-stu-id="9d497-108">Attributes</span></span>

<span data-ttu-id="9d497-109">없음</span><span class="sxs-lookup"><span data-stu-id="9d497-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d497-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9d497-110">Child Elements</span></span>

<span data-ttu-id="9d497-111">없음</span><span class="sxs-lookup"><span data-stu-id="9d497-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d497-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9d497-112">Parent Elements</span></span>

|<span data-ttu-id="9d497-113">요소</span><span class="sxs-lookup"><span data-stu-id="9d497-113">Element</span></span>|<span data-ttu-id="9d497-114">설명</span><span class="sxs-lookup"><span data-stu-id="9d497-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d497-115">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="9d497-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="9d497-116">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d497-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d497-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9d497-117">Text Value</span></span>

<span data-ttu-id="9d497-118">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d497-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d497-119">설명</span><span class="sxs-lookup"><span data-stu-id="9d497-119">Remarks</span></span>

<span data-ttu-id="9d497-120">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d497-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9d497-121">예제</span><span class="sxs-lookup"><span data-stu-id="9d497-121">Example</span></span>

<span data-ttu-id="9d497-122">이 예제에서는 `TableColumnItem` `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 지정 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9d497-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="9d497-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d497-123">See Also</span></span>

[<span data-ttu-id="9d497-124">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="9d497-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9d497-125">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="9d497-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="9d497-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9d497-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
