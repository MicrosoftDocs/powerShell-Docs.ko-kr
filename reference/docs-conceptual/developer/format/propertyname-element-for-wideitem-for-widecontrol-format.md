---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 WideItem에 대한 PropertyName 요소(형식)
description: WideControl의 WideItem에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665620"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="df4ca-103">WideControl의 WideItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="df4ca-103">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="df4ca-104">넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4ca-104">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="df4ca-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry element (format) WideItem Element (format) PropertyName Element for WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="df4ca-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df4ca-106">구문</span><span class="sxs-lookup"><span data-stu-id="df4ca-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df4ca-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="df4ca-107">Attributes and Elements</span></span>

<span data-ttu-id="df4ca-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="df4ca-108">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df4ca-109">특성</span><span class="sxs-lookup"><span data-stu-id="df4ca-109">Attributes</span></span>

<span data-ttu-id="df4ca-110">없음</span><span class="sxs-lookup"><span data-stu-id="df4ca-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df4ca-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="df4ca-111">Child Elements</span></span>

<span data-ttu-id="df4ca-112">없음</span><span class="sxs-lookup"><span data-stu-id="df4ca-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df4ca-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="df4ca-113">Parent Elements</span></span>

|<span data-ttu-id="df4ca-114">요소</span><span class="sxs-lookup"><span data-stu-id="df4ca-114">Element</span></span>|<span data-ttu-id="df4ca-115">설명</span><span class="sxs-lookup"><span data-stu-id="df4ca-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df4ca-116">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="df4ca-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="df4ca-117">값이 넓은 뷰에 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4ca-117">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="df4ca-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="df4ca-118">Text Value</span></span>

<span data-ttu-id="df4ca-119">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="df4ca-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="df4ca-120">설명</span><span class="sxs-lookup"><span data-stu-id="df4ca-120">Remarks</span></span>

<span data-ttu-id="df4ca-121">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="df4ca-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="df4ca-122">예제</span><span class="sxs-lookup"><span data-stu-id="df4ca-122">Example</span></span>

<span data-ttu-id="df4ca-123">이 예제에서는 ProcessName 개체의 속성 값을 표시 하는 넓은 보기를 보여 [줍니다.](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="df4ca-123">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="df4ca-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df4ca-124">See Also</span></span>

[<span data-ttu-id="df4ca-125">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="df4ca-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="df4ca-126">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="df4ca-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="df4ca-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="df4ca-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
