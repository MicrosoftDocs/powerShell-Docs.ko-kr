---
title: GroupBy (Format)의 Label 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365202"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="79c0a-102">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="79c0a-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="79c0a-103">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79c0a-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="79c0a-104">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) Label 요소</span><span class="sxs-lookup"><span data-stu-id="79c0a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79c0a-105">구문</span><span class="sxs-lookup"><span data-stu-id="79c0a-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79c0a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="79c0a-106">Attributes and Elements</span></span>

<span data-ttu-id="79c0a-107">다음 섹션에서는 `Label` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="79c0a-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79c0a-108">특성</span><span class="sxs-lookup"><span data-stu-id="79c0a-108">Attributes</span></span>

<span data-ttu-id="79c0a-109">없음</span><span class="sxs-lookup"><span data-stu-id="79c0a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79c0a-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="79c0a-110">Child Elements</span></span>

<span data-ttu-id="79c0a-111">없음</span><span class="sxs-lookup"><span data-stu-id="79c0a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79c0a-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="79c0a-112">Parent Elements</span></span>

|<span data-ttu-id="79c0a-113">요소</span><span class="sxs-lookup"><span data-stu-id="79c0a-113">Element</span></span>|<span data-ttu-id="79c0a-114">설명</span><span class="sxs-lookup"><span data-stu-id="79c0a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79c0a-115">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="79c0a-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="79c0a-116">새 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="79c0a-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79c0a-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="79c0a-117">Text Value</span></span>

<span data-ttu-id="79c0a-118">Windows PowerShell에서 새 속성이 나 스크립트 값을 발견할 때마다 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79c0a-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="79c0a-119">설명</span><span class="sxs-lookup"><span data-stu-id="79c0a-119">Remarks</span></span>

<span data-ttu-id="79c0a-120">이 요소에 지정 된 텍스트 외에도 Windows PowerShell은 그룹을 시작 하는 새 값을 표시 하 고 그룹 앞과 뒤에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="79c0a-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="79c0a-121">예제</span><span class="sxs-lookup"><span data-stu-id="79c0a-121">Example</span></span>

<span data-ttu-id="79c0a-122">다음 예에서는 새 그룹의 레이블을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79c0a-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="79c0a-123">표시 되는 레이블은 다음과 유사 합니다. `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="79c0a-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="79c0a-124">이 요소를 포함 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79c0a-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79c0a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79c0a-125">See Also</span></span>

[<span data-ttu-id="79c0a-126">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="79c0a-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="79c0a-127">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="79c0a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
