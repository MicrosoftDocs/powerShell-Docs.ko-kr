---
title: WideControl (Format)의 WideItem에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787600"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="37454-102">WideControl의 WideItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="37454-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="37454-103">넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37454-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="37454-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry Element (format) WideItem element (format) ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="37454-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37454-105">구문</span><span class="sxs-lookup"><span data-stu-id="37454-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37454-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="37454-106">Attributes and Elements</span></span>

<span data-ttu-id="37454-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="37454-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37454-108">특성</span><span class="sxs-lookup"><span data-stu-id="37454-108">Attributes</span></span>

<span data-ttu-id="37454-109">없음</span><span class="sxs-lookup"><span data-stu-id="37454-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37454-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="37454-110">Child Elements</span></span>

<span data-ttu-id="37454-111">없음</span><span class="sxs-lookup"><span data-stu-id="37454-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37454-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="37454-112">Parent Elements</span></span>

|<span data-ttu-id="37454-113">요소</span><span class="sxs-lookup"><span data-stu-id="37454-113">Element</span></span>|<span data-ttu-id="37454-114">설명</span><span class="sxs-lookup"><span data-stu-id="37454-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37454-115">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="37454-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="37454-116">값이 넓은 뷰에 표시 되는 속성 또는 스크립트 블록을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="37454-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37454-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="37454-117">Text Value</span></span>

<span data-ttu-id="37454-118">값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37454-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="37454-119">설명</span><span class="sxs-lookup"><span data-stu-id="37454-119">Remarks</span></span>

<span data-ttu-id="37454-120">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37454-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="37454-121">예제</span><span class="sxs-lookup"><span data-stu-id="37454-121">Example</span></span>

<span data-ttu-id="37454-122">이 예제에서는 `WideItem` 값이 뷰에 표시 되는 스크립트를 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37454-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="37454-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37454-123">See Also</span></span>

[<span data-ttu-id="37454-124">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="37454-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="37454-125">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="37454-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="37454-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="37454-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
