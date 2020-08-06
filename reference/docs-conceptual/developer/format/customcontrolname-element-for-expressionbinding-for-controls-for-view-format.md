---
title: 뷰 (형식)의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786019"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="e16e4-102">View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="e16e4-103">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e16e4-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="e16e4-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e16e4-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e16e4-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 view (format) CustomEntries 요소에 대 한 컨트롤 요소 (형식) Customentries view (format)의 컨트롤에 대 한 Customentries 요소의 Customentries 요소 뷰 (Format)의 컨트롤에 대 한 customentries 요소에 대 한 컨트롤의 customentries 요소에 대 한 컨트롤의 Customentries 요소</span><span class="sxs-lookup"><span data-stu-id="e16e4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e16e4-106">구문</span><span class="sxs-lookup"><span data-stu-id="e16e4-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e16e4-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e16e4-107">Attributes and Elements</span></span>

<span data-ttu-id="e16e4-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="e16e4-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e16e4-109">특성</span><span class="sxs-lookup"><span data-stu-id="e16e4-109">Attributes</span></span>

<span data-ttu-id="e16e4-110">없음</span><span class="sxs-lookup"><span data-stu-id="e16e4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e16e4-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e16e4-111">Child Elements</span></span>

<span data-ttu-id="e16e4-112">없음</span><span class="sxs-lookup"><span data-stu-id="e16e4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e16e4-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e16e4-113">Parent Elements</span></span>

|<span data-ttu-id="e16e4-114">요소</span><span class="sxs-lookup"><span data-stu-id="e16e4-114">Element</span></span>|<span data-ttu-id="e16e4-115">설명</span><span class="sxs-lookup"><span data-stu-id="e16e4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e16e4-116">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="e16e4-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e16e4-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e16e4-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e16e4-118">Text Value</span></span>

<span data-ttu-id="e16e4-119">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e16e4-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="e16e4-120">설명</span><span class="sxs-lookup"><span data-stu-id="e16e4-120">Remarks</span></span>

<span data-ttu-id="e16e4-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e16e4-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="e16e4-122">다음 요소는 이러한 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e16e4-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="e16e4-123">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="e16e4-124">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="e16e4-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e16e4-125">See Also</span></span>

[<span data-ttu-id="e16e4-126">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e16e4-127">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e16e4-128">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e16e4-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="e16e4-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e16e4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
