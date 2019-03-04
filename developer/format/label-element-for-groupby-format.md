---
title: GroupBy (형식)에 대 한 요소 레이블을 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862399"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="70bc0-102">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="70bc0-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="70bc0-103">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="70bc0-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 GroupBy (형식)에 대 한 보기 (형식) 레이블 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="70bc0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70bc0-105">구문</span><span class="sxs-lookup"><span data-stu-id="70bc0-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70bc0-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="70bc0-106">Attributes and Elements</span></span>

<span data-ttu-id="70bc0-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Label` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70bc0-108">특성</span><span class="sxs-lookup"><span data-stu-id="70bc0-108">Attributes</span></span>

<span data-ttu-id="70bc0-109">없음</span><span class="sxs-lookup"><span data-stu-id="70bc0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70bc0-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="70bc0-110">Child Elements</span></span>

<span data-ttu-id="70bc0-111">없음</span><span class="sxs-lookup"><span data-stu-id="70bc0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70bc0-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="70bc0-112">Parent Elements</span></span>

|<span data-ttu-id="70bc0-113">요소</span><span class="sxs-lookup"><span data-stu-id="70bc0-113">Element</span></span>|<span data-ttu-id="70bc0-114">설명</span><span class="sxs-lookup"><span data-stu-id="70bc0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70bc0-115">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="70bc0-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="70bc0-116">새 개체 그룹에 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70bc0-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="70bc0-117">Text Value</span></span>

<span data-ttu-id="70bc0-118">Windows PowerShell에서 새 속성 또는 스크립트 값을 발견 될 때마다 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="70bc0-119">설명</span><span class="sxs-lookup"><span data-stu-id="70bc0-119">Remarks</span></span>

<span data-ttu-id="70bc0-120">이 요소에 의해 지정 된 텍스트, 외에도 Windows PowerShell의 그룹을 시작 하 고 그룹 전후에 빈 줄을 추가 하는 새 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="70bc0-121">예제</span><span class="sxs-lookup"><span data-stu-id="70bc0-121">Example</span></span>

<span data-ttu-id="70bc0-122">다음 예제에서는 새 그룹의 레이블을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="70bc0-123">표시 된 레이블을 다음과 유사 하 게 보입니다. `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="70bc0-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="70bc0-124">이 요소를 포함 하는 전체 서식 파일의 예제를 보려면 [넓은 보기 (GroupBy)](./wide-view-groupby.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc0-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70bc0-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70bc0-125">See Also</span></span>

[<span data-ttu-id="70bc0-126">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="70bc0-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="70bc0-127">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="70bc0-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
