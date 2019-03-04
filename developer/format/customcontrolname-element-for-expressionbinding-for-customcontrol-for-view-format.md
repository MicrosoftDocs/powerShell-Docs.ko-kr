---
title: ExpressionBinding CustomControl 보려면 (형식)에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860439"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="2ef16-102">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2ef16-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="2ef16-103">공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="2ef16-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2ef16-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 CustomControl CustomEntries CustomItem 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 보기 (형식) CustomEntries 요소에 CustomEntry CustomItem (형식)에 대 한 식 바인딩의 CustomItem (형식) CustomControlName 요소에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ef16-106">구문</span><span class="sxs-lookup"><span data-stu-id="2ef16-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ef16-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-107">Attributes and Elements</span></span>

<span data-ttu-id="2ef16-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControlName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ef16-109">특성</span><span class="sxs-lookup"><span data-stu-id="2ef16-109">Attributes</span></span>

<span data-ttu-id="2ef16-110">없음</span><span class="sxs-lookup"><span data-stu-id="2ef16-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ef16-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-111">Child Elements</span></span>

<span data-ttu-id="2ef16-112">없음</span><span class="sxs-lookup"><span data-stu-id="2ef16-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ef16-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-113">Parent Elements</span></span>

|<span data-ttu-id="2ef16-114">요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-114">Element</span></span>|<span data-ttu-id="2ef16-115">설명</span><span class="sxs-lookup"><span data-stu-id="2ef16-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ef16-116">ExpressionBinding 요소 CustomItem (형식)</span><span class="sxs-lookup"><span data-stu-id="2ef16-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="2ef16-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ef16-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="2ef16-118">Text Value</span></span>

<span data-ttu-id="2ef16-119">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ef16-120">설명</span><span class="sxs-lookup"><span data-stu-id="2ef16-120">Remarks</span></span>

<span data-ttu-id="2ef16-121">형식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있습니다 하 고 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="2ef16-122">이러한 컨트롤의 이름은 다음 요소에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef16-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="2ef16-123">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="2ef16-124">뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="2ef16-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ef16-125">See Also</span></span>

[<span data-ttu-id="2ef16-126">구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2ef16-127">뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소</span><span class="sxs-lookup"><span data-stu-id="2ef16-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="2ef16-128">ExpressionBinding 요소 CustomItem (형식)</span><span class="sxs-lookup"><span data-stu-id="2ef16-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2ef16-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="2ef16-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
