---
title: CustomControl for View (Format)의 ExpressionBinding에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364112"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="d7a0c-102">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="d7a0c-103">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="d7a0c-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d7a0c-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl 요소에 대 한 view (format) Customentries 요소에 대 한 CustomControl for view (format) customentries 요소에 대 한 CustomEntries 요소 Customentry에 대 한 요소 Customentry에 대 한 요소 (형식) CustomControlName 요소의 customentry (형식)에 대 한 식 바인딩</span><span class="sxs-lookup"><span data-stu-id="d7a0c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7a0c-106">구문</span><span class="sxs-lookup"><span data-stu-id="d7a0c-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7a0c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d7a0c-107">Attributes and Elements</span></span>

<span data-ttu-id="d7a0c-108">다음 섹션에서는 `CustomControlName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7a0c-109">특성</span><span class="sxs-lookup"><span data-stu-id="d7a0c-109">Attributes</span></span>

<span data-ttu-id="d7a0c-110">없음</span><span class="sxs-lookup"><span data-stu-id="d7a0c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7a0c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d7a0c-111">Child Elements</span></span>

<span data-ttu-id="d7a0c-112">없음</span><span class="sxs-lookup"><span data-stu-id="d7a0c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7a0c-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d7a0c-113">Parent Elements</span></span>

|<span data-ttu-id="d7a0c-114">요소</span><span class="sxs-lookup"><span data-stu-id="d7a0c-114">Element</span></span>|<span data-ttu-id="d7a0c-115">설명</span><span class="sxs-lookup"><span data-stu-id="d7a0c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7a0c-116">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="d7a0c-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7a0c-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d7a0c-118">Text Value</span></span>

<span data-ttu-id="d7a0c-119">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7a0c-120">설명</span><span class="sxs-lookup"><span data-stu-id="d7a0c-120">Remarks</span></span>

<span data-ttu-id="d7a0c-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="d7a0c-122">이러한 컨트롤의 이름은 다음 요소로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7a0c-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="d7a0c-123">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d7a0c-124">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d7a0c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7a0c-125">See Also</span></span>

[<span data-ttu-id="d7a0c-126">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7a0c-127">View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d7a0c-128">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d7a0c-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7a0c-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d7a0c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
