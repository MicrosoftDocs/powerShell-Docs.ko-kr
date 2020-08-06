---
title: GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786002"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="3557a-102">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="3557a-103">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="3557a-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3557a-105">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl CustomControl for GroupBy (format) Customentries 요소에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 Customentries의 경우 groupby (형식)에 대 한 ExpressionBinding의 CustomControlName 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3557a-106">구문</span><span class="sxs-lookup"><span data-stu-id="3557a-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3557a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3557a-107">Attributes and Elements</span></span>

<span data-ttu-id="3557a-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .</span><span class="sxs-lookup"><span data-stu-id="3557a-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3557a-109">특성</span><span class="sxs-lookup"><span data-stu-id="3557a-109">Attributes</span></span>

<span data-ttu-id="3557a-110">없음</span><span class="sxs-lookup"><span data-stu-id="3557a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3557a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3557a-111">Child Elements</span></span>

<span data-ttu-id="3557a-112">없음</span><span class="sxs-lookup"><span data-stu-id="3557a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3557a-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3557a-113">Parent Elements</span></span>

|<span data-ttu-id="3557a-114">요소</span><span class="sxs-lookup"><span data-stu-id="3557a-114">Element</span></span>|<span data-ttu-id="3557a-115">설명</span><span class="sxs-lookup"><span data-stu-id="3557a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3557a-116">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3557a-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3557a-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3557a-118">Text Value</span></span>

<span data-ttu-id="3557a-119">컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3557a-120">설명</span><span class="sxs-lookup"><span data-stu-id="3557a-120">Remarks</span></span>

<span data-ttu-id="3557a-121">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="3557a-122">다음 요소는 이러한 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3557a-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="3557a-123">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="3557a-124">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="3557a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3557a-125">See Also</span></span>

[<span data-ttu-id="3557a-126">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3557a-127">View에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="3557a-128">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3557a-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="3557a-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3557a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
