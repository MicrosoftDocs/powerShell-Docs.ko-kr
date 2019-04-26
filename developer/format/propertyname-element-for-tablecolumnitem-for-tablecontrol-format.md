---
title: TableControl (형식)에 대 한 TableColumnItem PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064616"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="d88c2-102">TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d88c2-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="d88c2-103">값은 행의 열에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d88c2-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="d88c2-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) TableColumnItems 요소 (형식) TableColumnItem 요소 (형식) TableColumnItem (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="d88c2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d88c2-105">구문</span><span class="sxs-lookup"><span data-stu-id="d88c2-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d88c2-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d88c2-106">Attributes and Elements</span></span>

<span data-ttu-id="d88c2-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d88c2-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d88c2-108">특성</span><span class="sxs-lookup"><span data-stu-id="d88c2-108">Attributes</span></span>

<span data-ttu-id="d88c2-109">없음</span><span class="sxs-lookup"><span data-stu-id="d88c2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d88c2-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d88c2-110">Child Elements</span></span>

<span data-ttu-id="d88c2-111">없음</span><span class="sxs-lookup"><span data-stu-id="d88c2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d88c2-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d88c2-112">Parent Elements</span></span>

|<span data-ttu-id="d88c2-113">요소</span><span class="sxs-lookup"><span data-stu-id="d88c2-113">Element</span></span>|<span data-ttu-id="d88c2-114">설명</span><span class="sxs-lookup"><span data-stu-id="d88c2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d88c2-115">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d88c2-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="d88c2-116">속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d88c2-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d88c2-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d88c2-117">Text Value</span></span>

<span data-ttu-id="d88c2-118">값은 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d88c2-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d88c2-119">설명</span><span class="sxs-lookup"><span data-stu-id="d88c2-119">Remarks</span></span>

<span data-ttu-id="d88c2-120">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d88c2-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d88c2-121">예제</span><span class="sxs-lookup"><span data-stu-id="d88c2-121">Example</span></span>

<span data-ttu-id="d88c2-122">보여 주는이 예제는 `TableColumnItem` 지정 하는 요소를 `Status` 의 속성을 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d88c2-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="d88c2-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d88c2-123">See Also</span></span>

[<span data-ttu-id="d88c2-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="d88c2-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d88c2-125">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d88c2-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="d88c2-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d88c2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
