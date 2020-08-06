---
title: 뷰의 컨트롤에 대 한 CustomEntry 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785900"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="31ebd-102">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31ebd-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="31ebd-103">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-103">Provides a definition of the control.</span></span> <span data-ttu-id="31ebd-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="31ebd-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소에 대 한 컨트롤의 컨트롤에 대 한 CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="31ebd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31ebd-106">구문</span><span class="sxs-lookup"><span data-stu-id="31ebd-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31ebd-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="31ebd-107">Attributes and Elements</span></span>

<span data-ttu-id="31ebd-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="31ebd-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31ebd-109">특성</span><span class="sxs-lookup"><span data-stu-id="31ebd-109">Attributes</span></span>

<span data-ttu-id="31ebd-110">없음</span><span class="sxs-lookup"><span data-stu-id="31ebd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31ebd-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="31ebd-111">Child Elements</span></span>

|<span data-ttu-id="31ebd-112">요소</span><span class="sxs-lookup"><span data-stu-id="31ebd-112">Element</span></span>|<span data-ttu-id="31ebd-113">설명</span><span class="sxs-lookup"><span data-stu-id="31ebd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31ebd-114">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31ebd-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="31ebd-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="31ebd-116">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="31ebd-117">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31ebd-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="31ebd-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-118">Required element.</span></span><br /><br /> <span data-ttu-id="31ebd-119">컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="31ebd-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="31ebd-120">Parent Elements</span></span>

|<span data-ttu-id="31ebd-121">요소</span><span class="sxs-lookup"><span data-stu-id="31ebd-121">Element</span></span>|<span data-ttu-id="31ebd-122">설명</span><span class="sxs-lookup"><span data-stu-id="31ebd-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31ebd-123">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31ebd-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="31ebd-124">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ebd-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="31ebd-125">설명</span><span class="sxs-lookup"><span data-stu-id="31ebd-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="31ebd-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31ebd-126">See Also</span></span>

[<span data-ttu-id="31ebd-127">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31ebd-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="31ebd-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="31ebd-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
