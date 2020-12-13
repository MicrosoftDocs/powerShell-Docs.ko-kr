---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy에 대한 Label 요소(형식)
description: GroupBy에 대한 Label 요소(형식)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649793"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="5335a-103">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5335a-103">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="5335a-104">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5335a-104">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="5335a-105">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) Label 요소</span><span class="sxs-lookup"><span data-stu-id="5335a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5335a-106">구문</span><span class="sxs-lookup"><span data-stu-id="5335a-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5335a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5335a-107">Attributes and Elements</span></span>

<span data-ttu-id="5335a-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Label` .</span><span class="sxs-lookup"><span data-stu-id="5335a-108">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5335a-109">특성</span><span class="sxs-lookup"><span data-stu-id="5335a-109">Attributes</span></span>

<span data-ttu-id="5335a-110">없음</span><span class="sxs-lookup"><span data-stu-id="5335a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5335a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5335a-111">Child Elements</span></span>

<span data-ttu-id="5335a-112">없음</span><span class="sxs-lookup"><span data-stu-id="5335a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5335a-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5335a-113">Parent Elements</span></span>

|<span data-ttu-id="5335a-114">요소</span><span class="sxs-lookup"><span data-stu-id="5335a-114">Element</span></span>|<span data-ttu-id="5335a-115">설명</span><span class="sxs-lookup"><span data-stu-id="5335a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5335a-116">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5335a-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="5335a-117">새 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5335a-117">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5335a-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5335a-118">Text Value</span></span>

<span data-ttu-id="5335a-119">Windows PowerShell에서 새 속성이 나 스크립트 값을 발견할 때마다 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5335a-119">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="5335a-120">설명</span><span class="sxs-lookup"><span data-stu-id="5335a-120">Remarks</span></span>

<span data-ttu-id="5335a-121">이 요소에 지정 된 텍스트 외에도 Windows PowerShell은 그룹을 시작 하는 새 값을 표시 하 고 그룹 앞과 뒤에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5335a-121">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="5335a-122">예제</span><span class="sxs-lookup"><span data-stu-id="5335a-122">Example</span></span>

<span data-ttu-id="5335a-123">다음 예에서는 새 그룹의 레이블을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5335a-123">The following example shows the label for a new group.</span></span> <span data-ttu-id="5335a-124">표시 되는 레이블은 다음과 유사 합니다. `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="5335a-124">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="5335a-125">이 요소를 포함 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5335a-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5335a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5335a-126">See Also</span></span>

[<span data-ttu-id="5335a-127">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5335a-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5335a-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5335a-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
