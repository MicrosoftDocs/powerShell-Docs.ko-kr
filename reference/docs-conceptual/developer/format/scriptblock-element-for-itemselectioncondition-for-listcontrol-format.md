---
title: 이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787634"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="4084e-102">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4084e-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="4084e-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4084e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4084e-104">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4084e-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="4084e-105">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4084e-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="4084e-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for ListEntries (format) ListEntry element for이 listcontrol (format) element for ListItems (format) element for ListEntry (format)의 ListItem 요소에 대 한이 listcontrol (형식)에 대 한 ItemSelectionCondition 요소에 대 한 ListItems (형식)</span><span class="sxs-lookup"><span data-stu-id="4084e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4084e-107">구문</span><span class="sxs-lookup"><span data-stu-id="4084e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4084e-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4084e-108">Attributes and Elements</span></span>

<span data-ttu-id="4084e-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="4084e-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4084e-110">특성</span><span class="sxs-lookup"><span data-stu-id="4084e-110">Attributes</span></span>

<span data-ttu-id="4084e-111">없음</span><span class="sxs-lookup"><span data-stu-id="4084e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4084e-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4084e-112">Child Elements</span></span>

<span data-ttu-id="4084e-113">없음</span><span class="sxs-lookup"><span data-stu-id="4084e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4084e-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4084e-114">Parent Elements</span></span>

|<span data-ttu-id="4084e-115">요소</span><span class="sxs-lookup"><span data-stu-id="4084e-115">Element</span></span>|<span data-ttu-id="4084e-116">설명</span><span class="sxs-lookup"><span data-stu-id="4084e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4084e-117">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4084e-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="4084e-118">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4084e-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4084e-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4084e-119">Text Value</span></span>

<span data-ttu-id="4084e-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4084e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4084e-121">설명</span><span class="sxs-lookup"><span data-stu-id="4084e-121">Remarks</span></span>

<span data-ttu-id="4084e-122">이 요소를 사용 하는 경우 `PropertyName` 선택 조건을 정의할 때 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4084e-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4084e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4084e-123">See Also</span></span>

[<span data-ttu-id="4084e-124">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4084e-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
