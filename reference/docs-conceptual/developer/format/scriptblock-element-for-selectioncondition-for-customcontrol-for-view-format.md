---
title: CustomControl에 대 한 SelectionCondition의 ScriptBlock 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785407"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="864ef-102">View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="864ef-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="864ef-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="864ef-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="864ef-104">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="864ef-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="864ef-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="864ef-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="864ef-106">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) Customentries 요소에 대 한 CustomControl (Format) Customentries 요소에 대 한 CustomControl의 customentries 요소 (형식)의 경우 CustomControl for view (format) ScriptBlock 요소의 SelectionCondition for view (format)</span><span class="sxs-lookup"><span data-stu-id="864ef-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="864ef-107">구문</span><span class="sxs-lookup"><span data-stu-id="864ef-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="864ef-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="864ef-108">Attributes and Elements</span></span>

<span data-ttu-id="864ef-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="864ef-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="864ef-110">특성</span><span class="sxs-lookup"><span data-stu-id="864ef-110">Attributes</span></span>

<span data-ttu-id="864ef-111">없음</span><span class="sxs-lookup"><span data-stu-id="864ef-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="864ef-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="864ef-112">Child Elements</span></span>

<span data-ttu-id="864ef-113">없음</span><span class="sxs-lookup"><span data-stu-id="864ef-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="864ef-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="864ef-114">Parent Elements</span></span>

|<span data-ttu-id="864ef-115">요소</span><span class="sxs-lookup"><span data-stu-id="864ef-115">Element</span></span>|<span data-ttu-id="864ef-116">설명</span><span class="sxs-lookup"><span data-stu-id="864ef-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="864ef-117">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="864ef-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="864ef-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="864ef-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="864ef-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="864ef-119">Text Value</span></span>

<span data-ttu-id="864ef-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="864ef-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="864ef-121">설명</span><span class="sxs-lookup"><span data-stu-id="864ef-121">Remarks</span></span>

<span data-ttu-id="864ef-122">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="864ef-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="864ef-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="864ef-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="864ef-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="864ef-124">See Also</span></span>

[<span data-ttu-id="864ef-125">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="864ef-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="864ef-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="864ef-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
