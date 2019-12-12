---
title: 이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362102"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="356ec-102">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="356ec-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="356ec-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="356ec-104">이 스크립트가 `true`평가 되 면 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="356ec-105">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="356ec-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 ListEntries의이 listcontrol (Format) ListItems 요소 ListItems에 대 한이 listcontrol (format) ListItem 요소의 경우이 listcontrol (format)의 ListItem 요소에 대 한 itemselectioncondition 요소이 listcontrol의 ItemSelectionCondition (형식)</span><span class="sxs-lookup"><span data-stu-id="356ec-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="356ec-107">구문</span><span class="sxs-lookup"><span data-stu-id="356ec-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="356ec-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="356ec-108">Attributes and Elements</span></span>

<span data-ttu-id="356ec-109">다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="356ec-110">특성</span><span class="sxs-lookup"><span data-stu-id="356ec-110">Attributes</span></span>

<span data-ttu-id="356ec-111">없음</span><span class="sxs-lookup"><span data-stu-id="356ec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="356ec-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="356ec-112">Child Elements</span></span>

<span data-ttu-id="356ec-113">없음</span><span class="sxs-lookup"><span data-stu-id="356ec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="356ec-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="356ec-114">Parent Elements</span></span>

|<span data-ttu-id="356ec-115">요소</span><span class="sxs-lookup"><span data-stu-id="356ec-115">Element</span></span>|<span data-ttu-id="356ec-116">설명</span><span class="sxs-lookup"><span data-stu-id="356ec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="356ec-117">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="356ec-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="356ec-118">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="356ec-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="356ec-119">Text Value</span></span>

<span data-ttu-id="356ec-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="356ec-121">설명</span><span class="sxs-lookup"><span data-stu-id="356ec-121">Remarks</span></span>

<span data-ttu-id="356ec-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 `PropertyName` 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="356ec-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="356ec-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="356ec-123">See Also</span></span>

[<span data-ttu-id="356ec-124">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="356ec-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
