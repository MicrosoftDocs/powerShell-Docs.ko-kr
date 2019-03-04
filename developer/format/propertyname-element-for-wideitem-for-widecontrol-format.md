---
title: PropertyName 요소 WideControl (형식)에 대 한 WideItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860959"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1a2fd-102">WideControl의 WideItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1a2fd-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1a2fd-103">값은 넓은 보기에서 표시 된 개체의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a2fd-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="1a2fd-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) WideItem 요소 (형식) PropertyName 요소 WideItem (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="1a2fd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a2fd-105">구문</span><span class="sxs-lookup"><span data-stu-id="1a2fd-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a2fd-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1a2fd-106">Attributes and Elements</span></span>

<span data-ttu-id="1a2fd-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1a2fd-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a2fd-108">특성</span><span class="sxs-lookup"><span data-stu-id="1a2fd-108">Attributes</span></span>

<span data-ttu-id="1a2fd-109">없음</span><span class="sxs-lookup"><span data-stu-id="1a2fd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a2fd-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1a2fd-110">Child Elements</span></span>

<span data-ttu-id="1a2fd-111">없음</span><span class="sxs-lookup"><span data-stu-id="1a2fd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a2fd-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1a2fd-112">Parent Elements</span></span>

|<span data-ttu-id="1a2fd-113">요소</span><span class="sxs-lookup"><span data-stu-id="1a2fd-113">Element</span></span>|<span data-ttu-id="1a2fd-114">설명</span><span class="sxs-lookup"><span data-stu-id="1a2fd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a2fd-115">WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1a2fd-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1a2fd-116">속성 또는 값은 넓은 보기에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a2fd-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1a2fd-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1a2fd-117">Text Value</span></span>

<span data-ttu-id="1a2fd-118">값은 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a2fd-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a2fd-119">설명</span><span class="sxs-lookup"><span data-stu-id="1a2fd-119">Remarks</span></span>

<span data-ttu-id="1a2fd-120">넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1a2fd-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1a2fd-121">예제</span><span class="sxs-lookup"><span data-stu-id="1a2fd-121">Example</span></span>

<span data-ttu-id="1a2fd-122">ProcessName 속성 값을 표시 하는 넓은 보기를 보여 주는이 예제는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1a2fd-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1a2fd-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a2fd-123">See Also</span></span>

[<span data-ttu-id="1a2fd-124">WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1a2fd-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1a2fd-125">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="1a2fd-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1a2fd-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1a2fd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
