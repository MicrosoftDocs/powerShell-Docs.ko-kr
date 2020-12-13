---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 WideItem에 대한 FormatString 요소(형식)
description: WideControl의 WideItem에 대한 FormatString 요소(형식)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667881"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="9add3-103">WideControl의 WideItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9add3-103">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="9add3-104">속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9add3-104">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="9add3-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl element (format) WideEntries element (format) WideEntry Element for WideControl (format) WideItem 요소의 WideControl for WideItem (형식)</span><span class="sxs-lookup"><span data-stu-id="9add3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9add3-106">구문</span><span class="sxs-lookup"><span data-stu-id="9add3-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9add3-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9add3-107">Attributes and Elements</span></span>

<span data-ttu-id="9add3-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FormatString` .</span><span class="sxs-lookup"><span data-stu-id="9add3-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9add3-109">특성</span><span class="sxs-lookup"><span data-stu-id="9add3-109">Attributes</span></span>

<span data-ttu-id="9add3-110">없음</span><span class="sxs-lookup"><span data-stu-id="9add3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9add3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9add3-111">Child Elements</span></span>

<span data-ttu-id="9add3-112">없음</span><span class="sxs-lookup"><span data-stu-id="9add3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9add3-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9add3-113">Parent Elements</span></span>

|<span data-ttu-id="9add3-114">요소</span><span class="sxs-lookup"><span data-stu-id="9add3-114">Element</span></span>|<span data-ttu-id="9add3-115">설명</span><span class="sxs-lookup"><span data-stu-id="9add3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9add3-116">WideControl에 대한 WideItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9add3-116">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="9add3-117">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9add3-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9add3-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9add3-118">Text Value</span></span>

<span data-ttu-id="9add3-119">데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9add3-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="9add3-120">예를 들어이 패턴을 사용 하 여 [System. Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0: HH}: {0: mm} 형식의 속성 값에 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9add3-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="9add3-121">설명</span><span class="sxs-lookup"><span data-stu-id="9add3-121">Remarks</span></span>

<span data-ttu-id="9add3-122">형식 문자열은 테이블 뷰, 목록 뷰, 넓은 뷰 또는 사용자 지정 뷰를 만들 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9add3-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="9add3-123">뷰에 표시 되는 값의 서식을 지정 하는 방법에 대 한 자세한 내용은 [표시 된 데이터 서식 지정](./formatting-displayed-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9add3-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="9add3-124">넓은 보기에서 서식 문자열을 사용 하는 방법에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9add3-124">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9add3-125">예제</span><span class="sxs-lookup"><span data-stu-id="9add3-125">Example</span></span>

<span data-ttu-id="9add3-126">다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .</span><span class="sxs-lookup"><span data-stu-id="9add3-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="9add3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9add3-127">See Also</span></span>

[<span data-ttu-id="9add3-128">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="9add3-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9add3-129">WideControl에 대한 WideItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9add3-129">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="9add3-130">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9add3-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
