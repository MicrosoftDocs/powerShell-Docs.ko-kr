---
title: 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064427"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="29297-102">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="29297-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="29297-103">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29297-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="29297-104">이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29297-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="29297-105">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29297-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="29297-106">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry EntrySelectedBy 구성 (형식)에 대 한 컨트롤에 대 한 구성 (형식) SelectionCondition 요소에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식) 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="29297-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29297-107">구문</span><span class="sxs-lookup"><span data-stu-id="29297-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29297-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="29297-108">Attributes and Elements</span></span>

<span data-ttu-id="29297-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="29297-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29297-110">특성</span><span class="sxs-lookup"><span data-stu-id="29297-110">Attributes</span></span>

<span data-ttu-id="29297-111">없음</span><span class="sxs-lookup"><span data-stu-id="29297-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29297-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="29297-112">Child Elements</span></span>

<span data-ttu-id="29297-113">없음</span><span class="sxs-lookup"><span data-stu-id="29297-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29297-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="29297-114">Parent Elements</span></span>

|<span data-ttu-id="29297-115">요소</span><span class="sxs-lookup"><span data-stu-id="29297-115">Element</span></span>|<span data-ttu-id="29297-116">설명</span><span class="sxs-lookup"><span data-stu-id="29297-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29297-117">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="29297-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="29297-118">공용 컨트롤 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="29297-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29297-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="29297-119">Text Value</span></span>

<span data-ttu-id="29297-120">계산 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29297-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="29297-121">설명</span><span class="sxs-lookup"><span data-stu-id="29297-121">Remarks</span></span>

<span data-ttu-id="29297-122">선택 조건 최소 하나의 스크립트 또는 속성 이름을 평가 수행 하려면을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29297-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="29297-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="29297-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29297-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29297-124">See Also</span></span>

[<span data-ttu-id="29297-125">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="29297-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="29297-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="29297-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
