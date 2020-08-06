---
title: WideControl (형식)의 WideItem에 대 한 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7728f960a67faa99eaafb4a4934674e119b8af27
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780477"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="8e75f-102">WideControl의 WideItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8e75f-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="8e75f-103">넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e75f-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="8e75f-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry element (format) WideItem Element (format) PropertyName Element for WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8e75f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e75f-105">구문</span><span class="sxs-lookup"><span data-stu-id="8e75f-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e75f-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8e75f-106">Attributes and Elements</span></span>

<span data-ttu-id="8e75f-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="8e75f-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e75f-108">특성</span><span class="sxs-lookup"><span data-stu-id="8e75f-108">Attributes</span></span>

<span data-ttu-id="8e75f-109">없음</span><span class="sxs-lookup"><span data-stu-id="8e75f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e75f-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8e75f-110">Child Elements</span></span>

<span data-ttu-id="8e75f-111">없음</span><span class="sxs-lookup"><span data-stu-id="8e75f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e75f-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8e75f-112">Parent Elements</span></span>

|<span data-ttu-id="8e75f-113">요소</span><span class="sxs-lookup"><span data-stu-id="8e75f-113">Element</span></span>|<span data-ttu-id="8e75f-114">설명</span><span class="sxs-lookup"><span data-stu-id="8e75f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e75f-115">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8e75f-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="8e75f-116">값이 넓은 뷰에 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e75f-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8e75f-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="8e75f-117">Text Value</span></span>

<span data-ttu-id="8e75f-118">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e75f-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e75f-119">설명</span><span class="sxs-lookup"><span data-stu-id="8e75f-119">Remarks</span></span>

<span data-ttu-id="8e75f-120">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e75f-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e75f-121">예제</span><span class="sxs-lookup"><span data-stu-id="8e75f-121">Example</span></span>

<span data-ttu-id="8e75f-122">이 예제에서는 ProcessName 개체의 속성 값을 표시 하는 넓은 보기를 보여 [줍니다.](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="8e75f-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8e75f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e75f-123">See Also</span></span>

[<span data-ttu-id="8e75f-124">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8e75f-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="8e75f-125">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="8e75f-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8e75f-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8e75f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
