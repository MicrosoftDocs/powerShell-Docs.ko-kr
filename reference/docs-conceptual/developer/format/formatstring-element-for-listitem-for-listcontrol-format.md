---
title: 이 listcontrol (형식)의 ListItem 요소에 대 한 FormatString 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363022"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="c368a-102">ListControl의 ListItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c368a-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="c368a-103">속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="c368a-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소의이 listcontrol (format) ListItems 요소 (형식) 이 listcontrol의 ListItem 요소에 대 한이 listcontrol (Format) FormatString 요소에 대 한 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c368a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c368a-105">구문</span><span class="sxs-lookup"><span data-stu-id="c368a-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c368a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c368a-106">Attributes and Elements</span></span>

<span data-ttu-id="c368a-107">다음 섹션에서는 특성, 자식 요소 및 `FormatString` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c368a-108">특성</span><span class="sxs-lookup"><span data-stu-id="c368a-108">Attributes</span></span>

<span data-ttu-id="c368a-109">없음</span><span class="sxs-lookup"><span data-stu-id="c368a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c368a-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c368a-110">Child Elements</span></span>

<span data-ttu-id="c368a-111">없음</span><span class="sxs-lookup"><span data-stu-id="c368a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c368a-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c368a-112">Parent Elements</span></span>

|<span data-ttu-id="c368a-113">요소</span><span class="sxs-lookup"><span data-stu-id="c368a-113">Element</span></span>|<span data-ttu-id="c368a-114">설명</span><span class="sxs-lookup"><span data-stu-id="c368a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c368a-115">ListItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c368a-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="c368a-116">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c368a-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="c368a-117">Text Value</span></span>

<span data-ttu-id="c368a-118">데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="c368a-119">예를 들어이 패턴을 사용 하 여 [System. Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0: HH}: {0: mm} 형식의 속성 값에 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="c368a-120">설명</span><span class="sxs-lookup"><span data-stu-id="c368a-120">Remarks</span></span>

<span data-ttu-id="c368a-121">형식 문자열은 테이블 뷰, 목록 뷰, 넓은 뷰 또는 사용자 지정 뷰를 만들 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="c368a-122">뷰에 표시 되는 값의 서식을 지정 하는 방법에 대 한 자세한 내용은 [표시 된 데이터 서식 지정](./formatting-displayed-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c368a-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="c368a-123">목록 뷰에서 형식 문자열을 사용 하는 방법에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c368a-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c368a-124">예제</span><span class="sxs-lookup"><span data-stu-id="c368a-124">Example</span></span>

<span data-ttu-id="c368a-125">다음 예제에서는 `StartTime` 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c368a-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="c368a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c368a-126">See Also</span></span>

[<span data-ttu-id="c368a-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="c368a-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c368a-128">ListItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="c368a-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="c368a-129">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c368a-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
